---
title: / CLRUNMANAGEDCODECHECK (odeberte SuppressUnmanagedCodeSecurityAttribute) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/27/2018
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
ms.openlocfilehash: 9868f0c35f4a988ac8e0aee8076f232f86c04afd
ms.sourcegitcommit: 072e12d6b7a242765bdcc9afe4a14a284ade01fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50136277"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/ CLRUNMANAGEDCODECHECK (odeberte SuppressUnmanagedCodeSecurityAttribute)

**/ CLRUNMANAGEDCODECHECK** Určuje, že má linker doporučení se netýká <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> do vytvořeného v propojovacím programu `PInvoke` volání ze spravovaného kódu do nativních knihoven DLL.

## <a name="syntax"></a>Syntaxe

> **/ CLRUNMANAGEDCODECHECK**[**: NO**]

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení, linker použije **SuppressUnmanagedCodeSecurityAttribute** do vytvořeného v propojovacím programu `PInvoke` volání. Když **/CLRUNMANAGEDCODECHECK** je ve skutečnosti **SuppressUnmanagedCodeSecurityAttribute** se odebere. Chcete-li explicitně použít **SuppressUnmanagedCodeSecurityAttribute** do vytvořeného v propojovacím programu `PInvoke` volání, můžete použít **/CLRUNMANAGEDCODECHECK:NO**.

Propojovací program přidá pouze atribut na objekty, které jsou kompilovány pomocí **/CLR** nebo **/CLR: pure**. Ale **/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

A `PInvoke` volání je vygenerován linkerem, když linker nelze najít spravovaných symbolů pro uspokojení odkazem ze spravovaného volající ale můžete najít symbol nativní ke splnění tohoto odkazu. Další informace o `PInvoke`, naleznete v tématu [volání nativních funkcí ze spravovaného kódu](../../dotnet/calling-native-functions-from-managed-code.md).

Poznámka: Pokud používáte <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ve vašem kódu, byste měli explicitně nastavit **/CLRUNMANAGEDCODECHECK** odebrat **SuppressUnmanagedCodeSecurity** atribut. Je potenciální ohrožení zabezpečení, pokud obsahuje bitovou kopii **SuppressUnmanagedCodeSecurity** a **AllowPartiallyTrustedCallers** atributy.

Zobrazit [zabezpečené kódování pokyny pro nespravovaný kód](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) Další informace o důsledky použití **SuppressUnmanagedCodeSecurityAttribute**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **Linkeru** uzlu.

1. Vyberte **Upřesnit** stránku vlastností.

1. Upravit **CLR nespravovaného kódu zkontrolujte** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.

## <a name="see-also"></a>Viz také:

- [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)
- [Možnosti linkeru](../../build/reference/linker-options.md)
