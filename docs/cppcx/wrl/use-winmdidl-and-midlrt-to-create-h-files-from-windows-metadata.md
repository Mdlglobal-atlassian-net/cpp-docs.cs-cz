---
title: 'Postupy: Vytváření souborů .h z metadat Windows pomocí nástrojů winmdidl.exe a midlrt.exe'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
ms.openlocfilehash: 8288fc11fd53fdef423a57d0faefbaa7c06326aa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500433"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>Postupy: Vytváření souborů .h z metadat Windows pomocí nástrojů winmdidl.exe a midlrt.exe

Nástrojů winmdidl. exe a midlrt. exe povolují interakci na úrovni COM mezi nativním C++ kódem a prostředí Windows Runtime komponentami. Nástrojů winmdidl. exe přebírá jako vstup soubor. winmd obsahující metadata pro komponentu prostředí Windows Runtime a výstup souboru IDL. Midlrt. exe převede tento soubor IDL na hlavičkové soubory, C++ které může kód spotřebovat. Oba nástroje jsou spouštěny v příkazovém řádku.

Tyto nástroje můžete používat ve dvou hlavních scénářích:

- Vytváření vlastních souborů IDL a hlavičkových souborů tak C++ , aby aplikace zapsaná pomocí knihovny šablon prostředí Windows Runtime (WRL) mohla spotřebovat vlastní komponentu prostředí Windows Runtime.

- Generování proxy a zástupných souborů pro uživatelsky definované typy událostí v součásti prostředí Windows Runtime. Další informace najdete v tématu [vlastní události a přístupové objekty událostí v prostředí Windows runtimech součástech](/windows/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components).

Tyto nástroje se vyžadují jenom k analýze vlastních souborů. winmd. Soubory. idl a. h pro součásti operačního systému Windows jsou pro vás již vygenerovány. Ve výchozím nastavení jsou v Windows 8.1 umístěny v adresáři \Program Files (x86) \Windows Kits\8.1\Include\winrt\\.

## <a name="location-of-the-tools"></a>Umístění nástrojů

Ve výchozím nastavení se v [Windows 8.1, nástrojů winmdidl. exe a midlrt. exe nachází v adresáři C:\Program Files (x86)\\\Windows Kits\8.1. Verze nástrojů jsou také k dispozici ve složkách \bin\x86\ a \bin\x64\.

## <a name="winmdidl-command-line-arguments"></a>Argumenty příkazového řádku nástrojů winmdidl

```
Winmdidl.exe [/nologo] [/suppressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile
```

**/nologo**<br/>
Zabrání konzole zobrazovat zprávy copyrightu nástrojů winmdidl a číslo verze.

**/suppressversioncheck**<br/>
Nepoužívá se.

**/time**<br/>
Zobrazí celkovou dobu provádění ve výstupu konzoly.

**/OutDir:** <em>adresář</em><br/>
Určuje výstupní adresář. Pokud cesta obsahuje mezery, použijte uvozovky. Výchozí výstupní adresář je  *\<jednotka >* : \Users\\ *\<username >* \AppData\Local\VirtualStore\Program Files (x86) \Microsoft Visual Studio 12,0\\.

**/banner:** <em>soubor</em><br/>
Určuje soubor, který obsahuje vlastní text, který se má předřadit do výchozí zprávy o autorských právech a číslo verze nástrojů winmdidl v horní části generovaného souboru. idl. Pokud cesta obsahuje mezery, použijte uvozovky.

**/utf8**<br/>
Způsobí, že se soubor zformátuje jako UTF-8.

*Winmdfile*<br/>
Název souboru. winmd k analýze. Pokud cesta obsahuje mezery, použijte uvozovky.

## <a name="midlrt-command-line-arguments"></a>Argumenty příkazového řádku midlrt

Viz [komponenty midlrt a prostředí Windows Runtime](/windows/win32/Midl/midlrt-and-windows-runtime-components).

## <a name="examples"></a>Příklady

Následující příklad ukazuje příkaz nástrojů winmdidl na příkazovém řádku sady Visual Studio x86. Určuje výstupní adresář a soubor, který obsahuje speciální text banneru, který se má přidat do vygenerovaného souboru IDL.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0>winmdidl /nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\Test_for_winmdidl\test_for_winmdidl.winmd"`

Následující příklad ukazuje zobrazení konzoly z nástrojů winmdidl, které indikuje, že operace byla úspěšná.

**Generování c:\users\giraffe\documents\\\Test_for_winmdidl.idl**

V dalším kroku se midlrt spustí na vygenerovaném souboru IDL. Všimněte si, že argument **metadata_dir** je zadán za názvem souboru. idl. Cesta k \WinMetadata\ je povinná – jedná se o umístění pro Windows. winmd.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0> midlrt "c:\users\mblome\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"`

## <a name="remarks"></a>Poznámky

Výstupní soubor z operace nástrojů winmdidl má stejný název jako vstupní soubor, ale má příponu názvu souboru. idl.

Pokud vyvíjíte prostředí Windows Runtime komponentu, ke které bude přicházet z WRL, můžete zadat nástrojů winmdidl. exe a midlrt. exe, které se spustí jako kroky po sestavení, aby se soubory. idl a. h vygenerovaly v každém sestavení. Příklad naleznete v tématu [Vyvolávání událostí v prostředí Windows runtimech součástech](/windows/uwp/winrt-components/raising-events-in-windows-runtime-components).