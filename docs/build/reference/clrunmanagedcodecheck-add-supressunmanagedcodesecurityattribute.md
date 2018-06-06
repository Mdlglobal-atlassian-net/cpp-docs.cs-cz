---
title: / CLRUNMANAGEDCODECHECK (přidat atribut SupressUnmanagedCodeSecurityAttribute) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
dev_langs:
- C++
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d0a70ea74851d3a10f9d46b8289098d6fb3fe22
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705371"
---
# <a name="clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (Přidat atribut SupressUnmanagedCodeSecurityAttribute)

**/ CLRUNMANAGEDCODECHECK** Určuje, zda se uplatní linkeru <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> na linkeru generované `PInvoke` volání nativních knihoven DLL ze spravovaného kódu.

## <a name="syntax"></a>Syntaxe

> **/ CLRUNMANAGEDCODECHECK**[**: NE**]

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení, použije linkeru **SuppressUnmanagedCodeSecurityAttribute** na linkeru generované `PInvoke` volání. Když **/CLRUNMANAGEDCODECHECK** je v platnosti **SuppressUnmanagedCodeSecurityAttribute** není použita.

Atribut linkeru přidá jenom na objekty, které jsou kompilovat s **/CLR** nebo **/CLR: pure**. Ale **/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

A `PInvoke` volání je generován linkeru, když linkeru nelze najít symbol spravované vyhovět odkaz ze spravovaných volající ale můžete najít nativní symbol pro uspokojení tento odkaz. Další informace o `PInvoke`, najdete v části [volání nativních funkcí ze spravovaného kódu](../../dotnet/calling-native-functions-from-managed-code.md).

Všimněte si, že pokud používáte <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ve vašem kódu, byste měli explicitně nastavit **/CLRUNMANAGEDCODECHECK**. Pokud bitová kopie obsahuje atribut SuppressUnmanagedCodeSecurity i AllowPartiallyTrustedCallers je potenciální ohrožení zabezpečení.

V tématu [zabezpečené kódování pokyny pro nespravovaného kódu](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) Další informace o důsledky použití **SuppressUnmanagedCodeSecurityAttribute**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **Linkeru** uzlu.

1. Vyberte **Upřesnit** stránku vlastností.

1. Změnit **CLR nespravovaný kód zkontrolovat** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.

## <a name="see-also"></a>Viz také:

- [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)
- [Možnosti linkeru](../../build/reference/linker-options.md)
