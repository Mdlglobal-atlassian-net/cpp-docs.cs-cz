---
title: Práce se soubory a I/o (C + +/ CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- .NET Framework [C++], file handling
- files [C++], .NET Framework and
- I/O [C++], .NET Framework applications
- .NET Framework [C++], I/O
- files [C++], listing files
- directories [C++], listing files
- monitoring file system events
- FileSystemWatcher class, examples
- examples [C++], monitoring file system changes
- events [C++], monitoring
- file system events [C++]
- files [C++], binary
- binary files, reading in C++
- reading text files
- text files, reading
- files [C++], retrieving information about
- FileInfo class
- binary files, writing in C++
- files [C++], binary
- files [C++], text
- text files, writing in C++
ms.assetid: 3296fd59-a83a-40d4-bd4a-6096cc13101b
ms.openlocfilehash: 332e1d6d292e32dcf129b37c8c4a7857f0b5985f
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424311"
---
# <a name="file-handling-and-io-ccli"></a>Práce se soubory a vstupně-výstupní operace (C++/CLI)

Ukazuje různé operace se soubory pomocí rozhraní .NET Framework.

Následující témata ukazují použití tříd definovaných v <xref:System.IO> oboru názvů k provádění různých operací se soubory.

## <a name="enumerate"></a> Vytvoření výčtu souborů v adresáři

Následující příklad kódu ukazuje, jak načíst seznam souborů v adresáři. Kromě toho jsou vyjmenovány podadresáře. Následující příklad kódu používá <xref:System.IO.Directory.GetFiles%2A> <xref:System.IO.Directory.GetFiles%2A> a <xref:System.IO.Directory.GetDirectories%2A> metody k zobrazení obsahu adresáře C:\Windows.

### <a name="example"></a>Příklad

```cpp
// enum_files.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ folder = "C:\\";
   array<String^>^ dir = Directory::GetDirectories( folder );
   Console::WriteLine("--== Directories inside '{0}' ==--", folder);
   for (int i=0; i<dir->Length; i++)
      Console::WriteLine(dir[i]);

   array<String^>^ file = Directory::GetFiles( folder );
   Console::WriteLine("--== Files inside '{0}' ==--", folder);
   for (int i=0; i<file->Length; i++)
      Console::WriteLine(file[i]);

   return 0;
}
```

## <a name="monitor"></a> Sledování změn systému souborů

Následující příklad kódu používá <xref:System.IO.FileSystemWatcher> k registraci události pro odpovídající soubory vytvořené, změněné, odstraněný nebo přejmenovaný. Namísto dotazování pravidelně adresář pro změny souborů, můžete použít <xref:System.IO.FileSystemWatcher> třídy k vyvolání události při zjištění změny.

### <a name="example"></a>Příklad

```cpp
// monitor_fs.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::IO;

ref class FSEventHandler
{
public:
    void OnChanged (Object^ source, FileSystemEventArgs^ e)
    {
        Console::WriteLine("File: {0} {1}",
               e->FullPath, e->ChangeType);
    }
    void OnRenamed(Object^ source, RenamedEventArgs^ e)
    {
        Console::WriteLine("File: {0} renamed to {1}",
                e->OldFullPath, e->FullPath);
    }
};

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();

   if(args->Length < 2)
   {
      Console::WriteLine("Usage: Watcher.exe <directory>");
      return -1;
   }

   FileSystemWatcher^ fsWatcher = gcnew FileSystemWatcher( );
   fsWatcher->Path = args[1];
   fsWatcher->NotifyFilter = static_cast<NotifyFilters>
              (NotifyFilters::FileName |
               NotifyFilters::Attributes |
               NotifyFilters::LastAccess |
               NotifyFilters::LastWrite |
               NotifyFilters::Security |
               NotifyFilters::Size );

    FSEventHandler^ handler = gcnew FSEventHandler();
    fsWatcher->Changed += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Created += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Deleted += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Renamed += gcnew RenamedEventHandler(
            handler, &FSEventHandler::OnRenamed);

    fsWatcher->EnableRaisingEvents = true;

    Console::WriteLine("Press Enter to quit the sample.");
    Console::ReadLine( );
}
```

## <a name="read_binary"></a> Čtení z binárního souboru

Následující příklad kódu ukazuje, jak přečíst binární data ze souboru, pomocí dvou tříd z <xref:System.IO?displayProperty=fullName> obor názvů: <xref:System.IO.FileStream> a <xref:System.IO.BinaryReader>. <xref:System.IO.FileStream> představuje skutečný soubor. <xref:System.IO.BinaryReader> poskytuje rozhraní pro datový proud, který umožňuje binární přístup.

Příklad kódu načte soubor s názvem data.bin a obsahuje celá čísla v binárním formátu. Informace o tomto typu souboru, naleznete v tématu [jak: Zápis do binárního souboru (C + +/ CLI)](../dotnet/how-to-write-a-binary-file-cpp-cli.md).

### <a name="example"></a>Příklad

```cpp
// binary_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "data.bin";
   try
   {
      FileStream^ fs = gcnew FileStream(fileName, FileMode::Open);
      BinaryReader^ br = gcnew BinaryReader(fs);

      Console::WriteLine("contents of {0}:", fileName);
      while (br->BaseStream->Position < br->BaseStream->Length)
         Console::WriteLine(br->ReadInt32().ToString());

      fs->Close( );
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("File '{0}' not found", fileName);
      else
         Console::WriteLine("Exception: ({0})", e);
      return -1;
   }
   return 0;
}
```

## <a name="read_text"></a> Čtení z textového souboru

Následující příklad kódu ukazuje, jak otevřít a přečíst si jeden řádek textu souboru chvíli, s použitím <xref:System.IO.StreamReader> třídu, která je definována v <xref:System.IO?displayProperty=fullName> oboru názvů. Instance této třídy se používá k otevření textového souboru a pak <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> metoda se používá k načtení každého řádku.

Tento příklad kódu načte soubor s názvem textfile.txt, který obsahuje text. Informace o tomto typu souboru, naleznete v tématu [jak: Zápis do textového souboru (C + +/ CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md).

### <a name="example"></a>Příklad

```cpp
// text_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";
   try
   {
      Console::WriteLine("trying to open file {0}...", fileName);
      StreamReader^ din = File::OpenText(fileName);

      String^ str;
      int count = 0;
      while ((str = din->ReadLine()) != nullptr)
      {
         count++;
         Console::WriteLine("line {0}: {1}", count, str );
      }
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("file '{0}' not found", fileName);
      else
         Console::WriteLine("problem reading file '{0}'", fileName);
   }

   return 0;
}
```

## <a name="retrieve"></a> Načtení informací o souboru

Následující příklad kódu ukazuje, <xref:System.IO.FileInfo> třídy. Když máte k dispozici název souboru, můžete k načtení informací o souboru, jako je například velikost souboru, adresáře, úplný název a datum a čas vytvoření a poslední změny této třídy.

Tento kód načte informace o souboru pro Notepad.exe.

### <a name="example"></a>Příklad

```cpp
// file_info.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();
   if (args->Length < 2)
   {
      Console::WriteLine("\nUSAGE : file_info <filename>\n\n");
      return -1;
   }

   FileInfo^ fi = gcnew FileInfo( args[1] );

   Console::WriteLine("file size: {0}", fi->Length );

   Console::Write("File creation date:  ");
   Console::Write(fi->CreationTime.Month.ToString());
   Console::Write(".{0}", fi->CreationTime.Day.ToString());
   Console::WriteLine(".{0}", fi->CreationTime.Year.ToString());

   Console::Write("Last access date:  ");
   Console::Write(fi->LastAccessTime.Month.ToString());
   Console::Write(".{0}", fi->LastAccessTime.Day.ToString());
   Console::WriteLine(".{0}", fi->LastAccessTime.Year.ToString());

   return 0;
}
```

## <a name="write_binary"></a> Zápis do binárního souboru

Následující příklad kódu ukazuje, zápis binární data do souboru. Používá třídy <xref:System.IO> a <xref:System.IO.FileStream> z oboru názvů <xref:System.IO.BinaryWriter>. <xref:System.IO.FileStream> představuje skutečný soubor, zatímco <xref:System.IO.BinaryWriter> poskytuje rozhraní pro datový proud, který umožňuje binární přístup.

Následující příklad kódu zapíše soubor obsahující celá čísla v binárním formátu. Tento soubor lze číst pomocí kódu v [jak: Čtení z binárního souboru (C + +/ CLI)](../dotnet/how-to-read-a-binary-file-cpp-cli.md).

### <a name="example"></a>Příklad

```cpp
// binary_write.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   array<Int32>^ data = {1, 2, 3, 10000};

   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);
   BinaryWriter^ w = gcnew BinaryWriter(fs);

   try
   {
      Console::WriteLine("writing data to file:");
      for (int i=0; i<data->Length; i++)
      {
         Console::WriteLine(data[i]);
         w->Write(data[i]);
      }
   }
   catch (Exception^)
   {
     Console::WriteLine("data could not be written");
     fs->Close();
     return -1;
   }

   fs->Close();
   return 0;
}
```

## <a name="write_text"></a> Zápis do textového souboru

Následující příklad kódu ukazuje, jak vytvořit textový soubor a zapsat do něj pomocí text <xref:System.IO.StreamWriter> třída, která je definována v <xref:System.IO> oboru názvů. <xref:System.IO.StreamWriter> Konstruktor přebírá název souboru, který se má vytvořit. Pokud soubor existuje, je přepsán (Pokud nepředáte hodnotu True jako druhý <xref:System.IO.StringWriter> argument konstruktoru).

Soubor je poté naplněn pomocí <xref:System.IO.StreamWriter.Write%2A> a <xref:System.IO.TextWriter.WriteLine%2A> funkce.

### <a name="example"></a>Příklad

```cpp
// text_write.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";

   StreamWriter^ sw = gcnew StreamWriter(fileName);
   sw->WriteLine("A text file is born!");
   sw->Write("You can use WriteLine");
   sw->WriteLine("...or just Write");
   sw->WriteLine("and do {0} output too.", "formatted");
   sw->WriteLine("You can also send non-text objects:");
   sw->WriteLine(DateTime::Now);
   sw->Close();
   Console::WriteLine("a new file ('{0}') has been written", fileName);

   return 0;
}
```

## <a name="see-also"></a>Viz také

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[Souborová služba a Stream I/o](/dotnet/standard/io/index)

<xref:System.IO>