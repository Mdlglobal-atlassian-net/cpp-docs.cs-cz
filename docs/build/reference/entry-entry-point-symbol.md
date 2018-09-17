---
title: -ENTRY (Symbol vstupního bodu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
dev_langs:
- C++
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53f5a18b061cbd956731ced6788e86f871ea97bd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719573"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (symbol vstupního bodu)

```
/ENTRY:function
```

## <a name="arguments"></a>Arguments

*– funkce*<br/>
Funkce, která určuje uživatelský počáteční adresu souboru .exe nebo knihovny DLL.

## <a name="remarks"></a>Poznámky

/ Entry určuje funkci vstupního bodu jako počáteční adresu souboru .exe nebo knihovny DLL.

Funkce musí být definována pro použití `__stdcall` konvence volání. Parametry a vrácená hodnota závisí na Pokud program je konzolová aplikace, aplikace pro windows nebo knihovny DLL. Doporučuje se, že necháte linkeru nastavit vstupní bod tak, aby se správně inicializovat knihovny run-time jazyka C a C++ konstruktory pro statické objekty jsou spouštěny.

Ve výchozím nastavení je počáteční adresa názvu funkce z knihovny run-time C. Propojovacího programu vybere podle atributů program, jak je znázorněno v následující tabulce.

|Název funkce|Výchozí hodnoty pro|
|-------------------|-----------------|
|**mainCRTStartup** (nebo **wmainCRTStartup**)|Aplikace, která se používá/Subsystem: Console; volání `main` (nebo `wmain`)|
|**WinMainCRTStartup** (nebo **wWinMainCRTStartup**)|Aplikace, která se používá/Subsystem:**WINDOWS**; volání `WinMain` (nebo `wWinMain`), který musí být definován použití `__stdcall`|
|**_DllMainCRTStartup**|KNIHOVNY DLL; volání `DllMain` pokud existuje, které musí být definován použití `__stdcall`|

Pokud [/dll](../../build/reference/dll-build-a-dll.md) nebo [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) možnost není zadán, linker vybere subsystému a vstupního bodu podle toho, jestli `main` nebo `WinMain` je definována.

Funkce `main`, `WinMain`, a `DllMain` jsou tři formy uživatelem definované vstupní bod.

Při vytvoření spravované image, funkce určené k/Entry musí mít podpis z (lpvoid – *var1*, DWORD *var2*, lpvoid – *var3*).

Informace o tom, jak definovat vlastní `DllMain` vstupní bod, najdete v článku [Visual C++ a knihoven DLL knihovny run-time chování](../../build/run-time-library-behavior.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **Upřesnit** stránku vlastností.

1. Upravit **vstupní bod** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)