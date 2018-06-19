---
title: Soubory prostředků (Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio]
- .rc files
- resource files
- resource script files
- resource script files, Win-32 based applications
- resource script files, files updated when editing resources
- resources [Visual Studio], types of resource files
- rct files
- resources [C++]
- rc files
- resource files, types of
- .rct files
- resource script files, unsupported types
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b4b56d1f329aee29c37b15590729074d305f04d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879871"
---
# <a name="resource-files-visual-studio"></a>Zdrojové soubory (Visual Studio)
> [!NOTE]
>  Tomto materiálu se vztahuje na aplikací klasické pracovní plochy Windows. Informace o prostředcích v aplikacích pro univerzální platformu Windows najdete v tématu [definování prostředky aplikace](http://msdn.microsoft.com/en-us/476ea844-632c-4467-9ce3-966be1350dd4).  
>   
> Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
>  
> Vzhledem k tomu, že projekty v rozhraní .NET programovací jazyky nepoužívají soubory skriptu prostředků, musíte otevřít vaše prostředky z **Průzkumníku řešení**. Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pracovat se soubory prostředků v spravované projekty. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.  
  
 Termín "soubor prostředků" mohou odkazovat na určité typy souborů, včetně:  
  
-   Soubor skriptu (.rc) prostředku programu.  
  
-   Soubor šablony (.rct) prostředku.  
  
-   Jednotlivé zdroje existující jako samostatný soubor, jako je soubor rastrového obrázku, ikony nebo kurzoru, se označuje ze souboru .rc.  
  
-   Soubor hlavičky generované vývojového prostředí, například Resource.h, který je označován ze souboru .rc.  
  
 Prostředky je možné také najít v [typy souborů jiných](../windows/editable-file-types-for-resources.md) třeba soubory .exe, .dll a .res. Můžete pracovat s prostředky, soubory prostředků z projektu a ty, které nejsou součástí aktuálního projektu. Můžete také pracovat se soubory prostředků, které nebyly vytvořeny ve vývojovém prostředí sady Visual Studio. Například můžete:  
  
-   Práce se vnořené a podmíněně zahrnuté soubory prostředků.  
  
-   Aktualizace existujících prostředků nebo je převést na formát Visual C++.  
  
-   Importovat nebo exportovat grafických prostředků do nebo z aktuální soubor prostředků.  
  
-   Zahrnout sdílených nebo jen pro čtení identifikátorů (symboly), které nelze změnit pomocí vývojového prostředí.  
  
-   Během aktuálního projektu, například prostředky, které jsou sdíleny mezi několik projektů zahrnují prostředky v souboru spustitelný soubor (.exe), nevyžadují úpravy (nebo které nechcete, aby k provádění úprav).  
  
-   Zahrnete typy prostředků není podporován ve vývojovém prostředí.  
  
 Tato část zahrnuje:  
  
-   [Vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md)  
  
-   [Vytvoření nového prostředku](../windows/how-to-create-a-resource.md)  
  
-   [Zobrazení prostředků v souboru skriptu prostředků](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
  
-   [Otevírání v textovém formátu souboru skriptu prostředků](../windows/how-to-open-a-resource-script-file-in-text-format.md)  
  
-   [Doba kompilace zdrojů, včetně](../windows/how-to-include-resources-at-compile-time.md)  
  
-   [Kopírování prostředků](../windows/how-to-copy-resources.md)  
  
-   [Použití šablon prostředků (.rct)](../windows/how-to-use-resource-templates.md)  
  
-   [Import a export prostředků](../windows/how-to-import-and-export-resources.md)  
  
-   [Upravitelné typy souborů pro prostředky](../windows/editable-file-types-for-resources.md)  
  
-   [Soubory ovlivněné úpravou prostředku](../windows/files-affected-by-resource-editing.md)  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editory prostředků](../windows/resource-editors.md)   
 [Práce se zdrojovými soubory](../windows/working-with-resource-files.md)   
 [Nabídky a další prostředky](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)

