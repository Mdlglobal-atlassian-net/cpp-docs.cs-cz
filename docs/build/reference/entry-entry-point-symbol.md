---
title: /ENTRY (symbol vstupního bodu)
ms.date: 11/04/2016
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
ms.openlocfilehash: 0f3604ef75ce10928463c088e423615886555eda
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807855"
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

Pokud [/dll](dll-build-a-dll.md) nebo [/Subsystem](subsystem-specify-subsystem.md) možnost není zadán, linker vybere subsystému a vstupního bodu podle toho, jestli `main` nebo `WinMain` je definována.

Funkce `main`, `WinMain`, a `DllMain` jsou tři formy uživatelem definované vstupní bod.

Při vytvoření spravované image, funkce určené k/Entry musí mít podpis z (lpvoid – *var1*, DWORD *var2*, lpvoid – *var3*).

Informace o tom, jak definovat vlastní `DllMain` vstupní bod, najdete v článku [Visual C++ a knihoven DLL knihovny run-time chování](../run-time-library-behavior.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **Upřesnit** stránku vlastností.

1. Upravit **vstupní bod** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
