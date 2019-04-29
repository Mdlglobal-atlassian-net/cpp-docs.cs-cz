---
title: 'Postupy: Vytváření souborů .h z metadat windows pomocí winmdidl.exe a midlrt.exe'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
ms.openlocfilehash: b9016f05b82e3eb04474d370bd069e8008de5278
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398105"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>Postupy: Vytváření souborů .h z metadat windows pomocí winmdidl.exe a midlrt.exe

Winmdidl.exe a midlrt.exe umožňují úrovni modelu COM interakci mezi nativním kódu C++ a součásti prostředí Windows Runtime. Winmdidl.exe přijímá jako vstup soubor winmd, který obsahuje metadata pro součást prostředí Windows Runtime a vypíše souboru IDL. Midlrt.exe převede tento soubor IDL hlavičkové soubory, které využívají kódu jazyka C++. Oba nástroje spusťte na příkazovém řádku.

Pomocí těchto nástrojů v dva základní scénáře:

- Vytváření vlastních IDL a soubory hlaviček, tak, aby aplikace v jazyce C++ zapsány pomocí Windows Runtime šablony knihovny (WRL) můžou využívat vlastní součásti prostředí Windows Runtime.

- Generování proxy a zástupných procedur souborů pro typy definované uživatelem událostí v komponentě Windows Runtime. Další informace najdete v tématu [vlastní události a přístupových objektů událostí v součástech Runtime Windows](/windows/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components).

Tyto nástroje se vyžadují pouze pro analýzu soubory vlastní .winmd. Soubory .idl a .h pro součásti operačního systému Windows jsou již vygenerován za vás. Ve výchozím nastavení ve Windows 8.1, se nacházejí v \Program soubory (x86) \Windows Kits\8.1\Include\winrt\\.

## <a name="location-of-the-tools"></a>Umístění nástroje

Ve výchozím nastavení [Windows 8.1, winmdidl.exe a midlrt.exe se nacházejí v C:\Program Files (x86) \Windows Kits\8.1\\. Verze nástroje jsou k dispozici také v \bin\x86\ a \bin\x64\ složky.

## <a name="winmdidl-command-line-arguments"></a>Argumenty příkazového řádku Winmdidl

```
Winmdidl.exe [/nologo] [/suppressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile
```

**/nologo**<br/>
Zakazuje zobrazení konzoly winmdidl zprávu o autorských právech a čísla verze.

**/suppressversioncheck**<br/>
Nepoužívá se.

**/ čas**<br/>
Celková doba spuštění se zobrazí ve výstupu konzoly.

**/OutDir:**<em>dir</em><br/>
Určuje výstupní adresář. Pokud cesta obsahuje mezery, použijte uvozovky. Výchozí výstupní adresář je  *\<jednotku >*: \Users\\*\<uživatelské jméno >* \AppData\Local\VirtualStore\Program soubory (x86) \Microsoft Visual Studio 12.0\\.

**/ banner:**<em>souboru</em><br/>
Určuje soubor, který obsahuje vlastní text předřaďte na výchozí zprávu o autorských právech a čísla verze winmdidl v horní části souboru generovaného IDL. Pokud cesta obsahuje mezery, použijte uvozovky.

**/utf8**<br/>
Způsobí, že soubor, který má být ve formátu UTF-8.

*Winmdfile*<br/>
Název souboru .winmd analyzovat. Pokud cesta obsahuje mezery, použijte uvozovky.

## <a name="midlrt-command-line-arguments"></a>Argumenty příkazového řádku Midlrt

Zobrazit [MIDLRT a prostředí Windows Runtime komponenty](/windows/desktop/Midl/midlrt-and-windows-runtime-components).

## <a name="examples"></a>Příklady

Následující příklad ukazuje winmdidl příkazu na příkazovém řádku aplikace Visual Studio x86. Určuje výstupní adresář a soubor, který obsahuje speciální nápis pro přidání do generovaného souboru.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0>winmdidl /nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\Test_for_winmdidl\test_for_winmdidl.winmd"`

Další příklad ukazuje zobrazení konzoly z winmdidl, která označuje, že operace byla úspěšná.

**Generating c:\users\giraffe\documents\\\Test_for_winmdidl.idl**

V dalším kroku midlrt spouštět generovaného souboru IDL. Všimněte si, **metadata_dir** je zadán argument za názvem souboru IDL. Vyžaduje se cesta \WinMetadata\ – jedná se o umístění pro windows.winmd.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0> midlrt "c:\users\mblome\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"`

## <a name="remarks"></a>Poznámky

Výstupní soubor z operace winmdidl má stejný název jako vstupní soubor, ale má příponu názvu souboru IDL.

Pokud vyvíjíte komponenty prostředí Windows Runtime, která budou mít přístup z WRL, můžete zadat winmdidl.exe a midlrt.exe ke spuštění jako kroky po sestavení tak, aby IDL a .h souborů se generují u každého sestavení. Příklad najdete v tématu [Raising Events v součástech Runtime Windows](/windows/uwp/winrt-components/raising-events-in-windows-runtime-components).