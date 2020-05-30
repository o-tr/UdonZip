# UdonZip

[![Discord](https://img.shields.io/badge/Discord-Discord%20Support-blueviolet?logo=discord)](https://discord.gg/7xJdWNk) - Feel free to join if you have any bugs or questions!

UdonZip is a ZIP parser written in Udon for VRChat.
The purpose of this project is for it to be used as an API in other bigger projects.
This work is something the average VRChatter never will notice, but something the author hopes might be beneficial and make the life easier for world/game creators in VRChat.

An example use of this library is allowing the player to paste the entire contents of an zip file (e.g. game save file) into an Input field in VRC, and allowing the world to then parse the submitted data.
For this purpose a full XML library has already been implemented, which you can find [here, called UdonXML](https://github.com/Foorack/UdonXML).

## 🛠️ Setup

### Requirements

* Unity 2018.4.20f1
* VRCSDK3
* Latest [UdonSharp](https://github.com/Merlin-san/UdonSharp/blob/master/README.md)

### Installation

1. Go to [Releases](https://github.com/Foorack/UdonZip/releases) and download the latest release. The file should end with `unitypackage`. If you can't find it, ask for help on Discord.
2. Import the package into Unity with Assets > Import Package > Custom Package. This will import the files to `Resources > Foorack > UdonXML`.
3. Create an Empty GameObject in your Scene, name it `UdonXML` and assign it the UdonXML UdonBehaviour.

### Getting started

1. Declare a `public UdonZip udonZip;` variable in your program.
2. Assign it the value of the UdonZip GameObject in your scene.
3. Extract your Zip data file with Extract `udonZip.Extract(inputData);`. It will return an object.
4. The object returned represents the archive of the Zip, use it when executing other API functions such as `GetFile` or `GetFileData`.

### Example demo

```csharp
using UnityEngine;
using UdonSharp;

public class UdonZipTest : UdonSharpBehaviour
{
    public UdonZip udonZip;

    private string EXAMPLE_DATA_1 =
        "UEsDBBQAAAAAAPVljFD4cLMKBQAAAAUAAAAIAAAAdGVzdC50eHRIZWxsdVBLAQIUABQAAAAAAPVljFD4cLMKBQAAAAUAAAAIAAAAAAAAAAEAIAAAAAAAAAB0ZXN0LnR4dFBLBQYAAAAAAQABADYAAAArAAAAAAA";

    private string EXAMPLE_DATA_2 =
        "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";
    
    public void Start()
    {
        var data = EXAMPLE_DATA_2;
        // When you select "MIME Tools > Base64 Encode" it does it without padding
        // Append padding '=' if necessary until length is divisible by 4.
        while (data.Length % 4 != 0)
        {
            data += "=";
        }
        Debug.Log("data-length: " + data.Length);
        
        // Extract the ZIP file and give an archive representation object
        var archive = udonZip.Extract(Convert.FromBase64String(data));
        // Fetches the "File" representation object, containing data such as "last modified", CRC and extra fields. 
        var file = udonZip.GetFile(archive, "word/document.xml");
        // Fetches the actual file data, the raw bytes decompressed.
        //   The first time you access a file it will decompress it if necessary.
        //   The second time and on it will always return the already compressed data, making it significantly faster.
        var fileData = udonZip.GetFileData(file);
        // Efficiently converts the byte array to a string by casting each byte to char.
        char[] rawXmlData = new char[fileData.Length];
        for (var i = 0; i != fileData.Length; i++)
        {
            rawXmlData[i] = (char) fileData[i];
        }

        Debug.Log("data:" + new String(rawXmlData));
    }
}
```

![console output](https://i.imgur.com/cq5IStu.png)

## 📄 Documentation

### Extracting data

#### 🟣 object Extract(byte[] data)
Loads a Zip file into memory by extracting the provided input.

Returns null in case of parse failure. (no? this is lie)


### Reading data

#### 🔵 string[] GetFileNames(object archive)
Returns a string array of all file names. File names always include the full path.

#### 🔵 object GetFile(object archive, string filePath)
Returns a file object representing the file with given filePath.

#### 🔵 byte[] GetFileData(object data, int index)
Returns a `byte[]` containing the raw uncompressed data of the file.
The first time you access a file it will decompress it if necessary.
The second time and on it will always return the already compressed data, making it significantly faster.


## 🚛 Roadmap

* Allowing to write and package Zip files, allowing the creation of Zip files.
* Implementing CRC32 checksum verficiation of decompression.
* Better error handling. Right now it is sketchy if given invalid/corrupt input data.