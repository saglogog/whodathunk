+++
date = "2025-10-18T15:08:49+03:00"
draft = true
title = "My First Post"
description = "Syncing legacy OneDrive files: options and a Go CSV-driven copy script, plus tips for bulk transfer via a secondary PC and FreeFileSync. Includes sample code!!"
summary = "Syncing legacy OneDrive files: options and a Go CSV-driven copy script, plus tips for bulk transfer via a secondary PC and FreeFileSync. Includes sample code!!"
slug = "first-post"
tags = ['yorgos']
+++

## 1. Job requirements

This week they are making me sync the files from the old system to the new. The IT guy isn't helping me out. I *really* don't want to do this.

I have to either:
1. use a script I made and sync this stuff one by one or
2. use a second PC and sync all the OneDrive content using it to an external, large enough drive and then sync the specific folders using FreeFileSync.

You can find the script here at the end of the post. Jump to [script](#script).

## 2. The grad programme

I reaaally am not sure about this.

## Test image

A test image follows.

{{< details summary="See the image" >}}

![alt text](drop-your-hardest-jjk-wallpaper-v0-jr7a37h6m0hc1.webp)

{{< /details >}}


## Script

This is a script I frankensteined from various stack overflow sources.

{{< details summary="See the script" >}}



```go 
package main

import (
	"encoding/csv"
	"fmt"
	"io"
	"log"
	"os"
)

func CopyFile(src, dst string) (err error){
	
	sfi, err := os.Stat(src)
	if err != nil{
		return
	}
	if !sfi.Mode().IsRegular() {
        // cannot copy non-regular files (e.g., directories,
        // symlinks, devices, etc.)
        return fmt.Errorf("CopyFile: non-regular source file %s (%q)", sfi.Name(), sfi.Mode().String())
    }

	dfi, err := os.Stat(dst)
    if err != nil {
        if !os.IsNotExist(err) {
            return
        }
		} else {
        // if !(dfi.Mode().IsRegular()) {
        //     return fmt.Errorf("CopyFile: non-regular destination file %s (%q)", dfi.Name(), dfi.Mode().String())
        // }
        if os.SameFile(sfi, dfi) {
            return
        }
    }

	copyFileContents(src, dst)
	
    return
}

func copyFileContents(src, dst string) (err error) {

	    in, err := os.Open(src)
    if err != nil {
        return
    }
    defer in.Close()
    out, err := os.Create(dst)
    if err != nil {
        return
    }
    defer func() {
        cerr := out.Close()
        if err == nil {
            err = cerr
        }
    }()
    if _, err = io.Copy(out, in); err != nil {
        return
    }
    err = out.Sync()
    return
}

func readCsvFile(filePath string) [][]string {
    f, err := os.Open(filePath)
    if err != nil {
        log.Fatal("Unable to read input file " + filePath, err)
    }
    defer f.Close()

    csvReader := csv.NewReader(f)
    csvReader.Comma = ';'
    records, err := csvReader.ReadAll()
    if err != nil {
        log.Fatal("Unable to parse file as CSV for " + filePath, err)
    }

    return records
}

func main() {
	// readCsvFile returns a string slice of slices ([][]string), CSV.ReadAll returns a slice of fields
    records := readCsvFile("./tbf3.csv")
	
	for i, v := range records{
		err := CopyFile(v[0], v[1])
		if err != nil {
			fmt.Printf("CopyFile failed %[1]q in line %[2]d\n", err, i)
		} else {
			fmt.Printf("CopyFile succeeded in line %[1]d\n", i)
		}
	}
    // for each record, make the copy from the record left side to the record right side
    // log all output


    // fmt.Println(records)
}


// func main() {
//     fmt.Printf("Copying %s to %s\n", os.Args[1], os.Args[2])
//     err := CopyFile(os.Args[1], os.Args[2])
//     if err != nil {
//         fmt.Printf("CopyFile failed %q\n", err)
//     } else {
//         fmt.Printf("CopyFile succeeded\n")
//     }
// }

```

{{< /details >}}
