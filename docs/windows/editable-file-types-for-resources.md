---
title: Upravitelné typy souboru pro prostředky (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: c40f9204-f2f2-400b-9f53-53b7bf291356
ms.openlocfilehash: 9f688c144a3453c2de849b36f34f6a465e3dfeae
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905716"
---
# <a name="editable-file-types-for-resources-c"></a>Upravitelné typy souboru pro prostředky (C++)

Můžete otevřít následující typy souborů a upravit prostředky, které obsahují.

|Název souboru|Popis|
|---------------|-----------------|
|.rc|Soubory skriptu prostředků.|
|.RCT|Soubory prostředků šablon.|
|.res|Soubory prostředků.|
|.resx|Spravovaných zdrojových souborů.|
|.exe|Spustitelné soubory.|
|.dll|Soubory knihoven DLL.|
|.bmp, ICO, DIB a .cur|Rastrový obrázek, ikona, nástrojů a kurzoru soubory.|

## <a name="files-affected-by-resource-editing"></a>Soubory ovlivněné úpravou prostředku

Prostředí sady Visual Studio spolupracuje s souborů, které jsou uvedené v následující tabulce během vaší relace úpravy prostředků.

|Název souboru|Popis|
|---------------|-----------------|
|Resource.h|Soubor hlaviček generovaných vývojové prostředí; obsahuje definice symbolů. (Zahrnout tento soubor do správy zdrojového kódu.)|
|Filename.aps|Binární verze aktuálního souboru skriptu prostředků; používá se pro rychlé načítání.<br /><br /> Editory prostředků přímo číst soubory .rc nebo souboru resource.h. Nástroj resource compiler jejich kompiluje do soubory .aps, které se spotřebovávají editory prostředků. Tento soubor je kompilační krok a ukládá pouze datový symbolické. Jako normální zkompilovat procesu, se zahodí informace, které nejsou symbolické (například komentáře) v průběhu kompilace. Pokaždé, když se soubor .aps získá synchronizována se soubor .rc, se znovu vygeneroval soubor .rc (například když uložíte, editor prostředků přepíše soubor .rc a soubor resource.h). Všechny změny samotné prostředky zůstanou zahrnuté v souboru .rc, ale komentáře vždy ztratí dojde k přepsání souboru .rc. Informace o tom, jak zachovat komentáře, naleznete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md). (Obvykle, nezahrnujte .aps soubor ve správě zdrojového kódu.)|
|.rc|Soubor skriptu prostředků, který obsahuje skript pro prostředky v aktuálním projektu. Tento soubor se přepíše souborem .aps při každém uložení. (Zahrnout tento soubor do správy zdrojového kódu.)|

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Soubory prostředků](../windows/resource-files-visual-studio.md)