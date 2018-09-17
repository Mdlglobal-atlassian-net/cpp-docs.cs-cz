---
title: -hotpatch (vytvoření Image vyměnitelné za provozu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- C++
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97e1b6197ea60099457db7788ad7e24b96c9fcb8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716967"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (Vytvořit bitovou kopii s možností provádění oprav za běhu)

Připravuje obrázek na horké záplatování.

## <a name="syntax"></a>Syntaxe

```
/hotpatch
```

## <a name="remarks"></a>Poznámky

Když **/hotpatch** se používá v kompilaci kompilátor zajišťuje, že první instrukce pro každou funkci je minimálně o dva bajty, které jsou požadovány pro technologii hot patching.

K dokončení přípravy pro zezáplatovatelnění obrazu, když použijete **/hotpatch** kompilace, je nutné použít [/FUNCTIONPADMIN (vytvoření Image vyměnitelné za provozu)](../../build/reference/functionpadmin-create-hotpatchable-image.md) propojení. Když kompilujete a propojujete obrázek s pomocí jednoho vyvolání cl.exe, **/hotpatch** znamená **/functionpadmin**.

Protože pokyny jsou vždy dva bajty nebo více v ARM architektuře a protože x64 kompilace je vždy brána jako **/hotpatch** byl zadán, není nutné zadat **/hotpatch** při kompilaci pro tyto cíle; však musí i nadále propojíte s použitím **/functionpadmin** k vytvoření Image vyměnitelné za provozu pro ně. **/Hotpatch** kompilátoru možnost pouze ovlivňuje x86 kompilace.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **C/C++** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. Přidat možnost kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="guidance"></a>Doprovodné materiály

Další informace o správě aktualizací najdete v tématu "Bezpečnostní pokyny pro správu aktualizací" na [ http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx ](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx).

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)