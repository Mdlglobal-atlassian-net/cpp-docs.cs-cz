---
title: "Editor informací o verzi | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.version.F1
dev_langs:
- C++
helpviewer_keywords:
- Version Information editor, about Version Information editor
- editors, Version Information
- resource editors, Version Information editor
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c221120bf7170025506fe49fe2ab6419ce66044
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="version-information-editor"></a>Editor informací o verzi
Informace o verzi se skládá z společnosti a identifikaci produktu, číslo verze produktu a oznámení o autorských právech a ochranná známka. Pomocí editoru informací o verzi můžete vytvořit a udržovat tato data, která je uložena v prostředku informací o verzi. Prostředku informací o verzi není vyžadována danou aplikací, ale je to užitečné místo shromažďovat informace, které identifikují aplikace. Informace o verzi se také používá při instalaci rozhraní API.  
  
 Prostředku informací o verzi má bloku horní a dolní bloky jeden nebo více: jeden blok informací v horní části a jeden nebo více verze bloků s informacemi o dole (pro jiné jazyky nebo znaků). Začátek bloku má upravovat číselná pole a vybrat rozevírací seznamy. Nižší bloky obsahují pouze upravitelných textových polí.  
  
> [!NOTE]
>  Windows standard je prostředek jenom jedna verze, s názvem VS_VERSION_INFO.  
  
 Informace o verzi editor umožňuje:  
  
-   [Úprava řetězce v prostředku informací o verzi](../windows/editing-a-string-in-a-version-information-resource.md)  
  
-   [Přidat informace o verzi pro jiný jazyk (nový blok informací o verzi)](../windows/adding-version-information-for-another-language.md)  
  
-   [Odstranění bloku informací o verzi](../windows/deleting-a-version-information-block.md)  
  
-   [Informace o verzi přístup z programu](../windows/accessing-version-information-from-within-your-program.md)  
  
    > [!NOTE]
    >  Při použití editoru informací o verzi, v mnoha případech je můžete kliknout pravým tlačítkem zobrazení místní nabídky příkazů konkrétní prostředky. Například pokud klepnete na při přejdete na položku záhlaví bloku, v místní nabídce zobrazuje příkazy nový blok informací o verzi a odstranění bloku informací o verzi služby.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editory prostředků](../windows/resource-editors.md)   
 [Nabídky a další prostředky](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)

