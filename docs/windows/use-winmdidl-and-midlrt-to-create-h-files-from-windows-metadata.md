---
title: 'Postupy: vytváření souborů .h z metadat windows pomocí winmdidl.exe a midlrt.exe | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 06fef7449a540fbd3cddc2d38c9ce7483a7b5d55
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891718"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>Postupy: Vytváření souborů .h z metadat Windows pomocí nástrojů winmdidl.exe a midlrt.exe
Winmdidl.exe a midlrt.exe povolit COM úrovni interakce mezi nativního kódu C++ a prostředí Windows Runtime součásti. Winmdidl.exe přijímá jako vstup .winmd soubor, který obsahuje metadata pro součást prostředí Windows Runtime a uloží soubor IDL. Midlrt.exe převede tento soubor IDL hlavičkových souborů, které můžou využívat kódu C++. Oba nástroje spusťte na příkazovém řádku.  
  
 Pomocí těchto nástrojů v dva základní scénáře:  
  
-   Vytváření vlastních IDL a hlavičkových souborů tak, aby aplikace na C++ zapsány pomocí Windows Runtime šablony knihovny (WRL) můžete využívat vlastní komponenty prostředí Windows Runtime.  
  
-   Generování proxy a se zakázaným inzerováním souborech typů událostí uživatelem definované v komponent prostředí Windows Runtime. Další informace najdete v tématu [vlastní události a přístupových objektů událostí v modulu Runtime součásti systému Windows](/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components).  
  
 Tyto nástroje se vyžaduje jenom pro analýza vlastní .winmd souborů. Soubory .idl a .h pro součásti systému Windows jsou pro vás již vygenerován. Ve výchozím nastavení v [!INCLUDE[win81](../misc/includes/win81_md.md)], se nacházejí v \Program soubory (x86) \Windows Kits\8.1\Include\winrt\\.  
  
## <a name="location-of-the-tools"></a>Umístění nástrojů  
 Ve výchozím nastavení v [!INCLUDE[win81](../misc/includes/win81_md.md)], winmdidl.exe a midlrt.exe se nacházejí v C:\Program Files (x86) \Windows Kits\8.1\\. Verze nástroje jsou k dispozici také v \bin\x86\ a \bin\x64\ složky.  
  
## <a name="winmdidl-command-line-arguments"></a>Argumenty příkazového řádku Winmdidl  
  
```  
Winmdidl.exe [/nologo] [/supressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile  
```  
  
 `/nologo`  
 Zabrání zobrazení konzoly winmdidl zpráva o autorských právech a číslo verze.  
  
 `/supressversioncheck`  
 Nepoužívá se.  
  
 `/time`  
 Zobrazí celkový čas spuštění ve výstupu konzoly.  
  
 Company:\<dir >  
 Určuje cílový adresář. Pokud cesta obsahuje mezery, použijte uvozovky. Výchozí adresář výstupu  *\<jednotky >*: \Users\\*\<uživatelské jméno >* \AppData\Local\VirtualStore\Program soubory (x86) \Microsoft Visual Studio 12.0\\.  
  
 `/banner:<file>`  
 Určuje soubor, který obsahuje vlastní text pro předřazení výchozí zprávu o autorských právech a číslo verze winmdidl v horní části souboru generovaného IDL. Pokud cesta obsahuje mezery, použijte uvozovky.  
  
 `/utf8`  
 Způsobí, že soubor má být formátována jako UTF-8.  
  
 `Winmdfile`  
 Název souboru .winmd analyzovat. Pokud cesta obsahuje mezery, použijte uvozovky.  
  
## <a name="midlrt-command-line-arguments"></a>Argumenty příkazového řádku Midlrt  
 V tématu [MIDLRT a prostředí Windows Runtime součásti](http://msdn.microsoft.com/library/windows/desktop/hh869900\(v=vs.85\).aspx).  
  
## <a name="examples"></a>Příklady  
 Následující příklad ukazuje winmdidl příkaz na příkazovém řádku Visual Studio x86. Určuje výstupní adresář a soubor, který obsahuje text speciální hlavičky k přidání do souboru generovaného .idl.  
  
 **C:\Program Files (x86) \Microsoft Visual Studio 12.0 > winmdidl/nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\ Test_for_winmdidl\test_for_winmdidl.winmd"**  
  
 Další příklad ukazuje zobrazení konzoly z winmdidl, která určuje, že operace byla úspěšná.  
  
 **Generování c:\users\giraffe\documents\\\Test_for_winmdidl.idl**  
  
 V dalším kroku midlrt běží na vygenerovaný soubor IDL. Všimněte si, že **metadata_dir** po název souboru .idl je zadán argument. Je vyžadována cesta \WinMetadata\ – je umístění windows.winmd.  
  
 **C:\Program Files (x86) \Microsoft Visual Studio 12.0 > midlrt "c:\users\mblome\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"**  
  
## <a name="remarks"></a>Poznámky  
 Výstupní soubor z operace winmdidl má stejný název jako vstupní soubor ale má příponu názvu souboru .idl.  
  
 Pokud vyvíjíte komponenty prostředí Windows Runtime, která bude přístupná z WRL, můžete zadat winmdidl.exe a midlrt.exe ke spuštění jako kroky následující po sestavení tak, aby soubory .idl a .h se generují u každé sestavení. Příklad, naleznete v části [vyvolání události v modulu Runtime součásti systému Windows](/uwp/winrt-components/raising-events-in-windows-runtime-components).