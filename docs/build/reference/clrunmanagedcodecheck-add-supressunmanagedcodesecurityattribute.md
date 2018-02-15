---
title: "-CLRUNMANAGEDCODECHECK (přidat atribut SupressUnmanagedCodeSecurityAttribute) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRUNMANAGEDCODECHECK
dev_langs:
- C++
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f32ae791ebb09d3d2cfced48c42f982580e69b63
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (Přidat atribut SupressUnmanagedCodeSecurityAttribute)
**/ CLRUNMANAGEDCODECHECK** Určuje, zda se uplatní linkeru <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> na linkeru generované `PInvoke` volání nativních knihoven DLL ze spravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/CLRUNMANAGEDCODECHECK[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, použije linkeru SuppressUnmanagedCodeSecurityAttribute vytvořit linkeru `PInvoke` volání. Když **/CLRUNMANAGEDCODECHECK** je ve skutečnosti SuppressUnmanagedCodeSecurityAttribute není použita.  
  
 Atribut linkeru přidá jenom na objekty, které jsou kompilovat s **/CLR** nebo **/CLR: pure**. Ale **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a bude v budoucí verzi systému kompilátoru odebrána.  
  
 A `PInvoke` volání je generován linkeru, když linkeru nelze najít symbol spravované vyhovět odkaz ze spravovaných volající ale můžete najít nativní symbol pro uspokojení tento odkaz. Další informace o `PInvoke`, najdete v části [volání nativních funkcí ze spravovaného kódu](../../dotnet/calling-native-functions-from-managed-code.md).  
  
 Všimněte si, že pokud používáte <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ve vašem kódu, byste měli explicitně nastavit **/CLRUNMANAGEDCODECHECK**. Pokud bitová kopie obsahuje atribut SuppressUnmanagedCodeSecurity i AllowPartiallyTrustedCallers je potenciální ohrožení zabezpečení.  
  
 V tématu [zabezpečené kódování pokyny pro nespravovaného kódu](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) Další informace o důsledky použití SuppressUnmanagedCodeSecurityAttribute.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **Upřesnit** stránku vlastností.  
  
5.  Změnit **CLR nespravovaný kód zkontrolovat** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)