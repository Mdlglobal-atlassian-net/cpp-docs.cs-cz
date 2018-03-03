---
title: "Binární Editor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.binary.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, Binary
- resources [Visual Studio], editing
- resource editors, Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4dade674fb32615e23904e6dbaf03d6c6ee0a371
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="binary-editor"></a>Binární editor
> [!WARNING]
>  Binární editor není dostupný ve verzích Express.  
  
 Binární editor umožňuje upravovat libovolný prostředek na binární úrovni v šestnáctkovém formátu nebo ve formátu ASCII. Můžete také [najít – příkaz](/visualstudio/ide/reference/find-command) k vyhledání řetězců ASCII nebo hexadecimální bajty. Binární editor by měl být použit pouze v případě, že je zapotřebí zobrazit nebo mírně upravit vlastní prostředky nebo typy prostředků, které nejsou podporovány prostředím Visual Studio.  
  
 Otevřete Editor pro binární, nejprve vyberte **soubor &#124; Nové &#124; Soubor** z hlavní nabídky, vyberte soubor, který chcete upravit, a potom klikněte na rozevírací šipku vedle položky **otevřete** tlačítko a zvolte **otevřít v &#124; Binární Editor**.  
  
> [!CAUTION]
>  Úprava prostředků jako dialogová okna, obrázky nebo nabídky pomocí binárního editoru není bezpečná. Nesprávné úpravy mohou prostředek poškodit a učinit jej nečitelným v jeho nativním editoru.  
  
> [!TIP]
>  Při používání binárního editoru lze v mnoha případech kliknout pravým tlačítkem myši a zobrazit místní nabídku příkazů specifických pro daný prostředek. Dostupné příkazy závisí na položce, na kterou právě ukazuje kurzor. Například pokud klepnete na při odkazující na binární editor s vybranou šestnáctkové hodnoty, místní nabídky ukazuje **Vyjmout**, **kopie**, a **vložení** příkazy.  
  
 Pomocí binárního editoru lze:  
  
-   [Otevření prostředku pro binární úpravy](../windows/opening-a-resource-for-binary-editing.md)  
  
-   [Upravit binární data](../windows/editing-binary-data.md)  
  
-   [Najít binární data](../windows/finding-binary-data.md)  
  
-   [Vytvoření nového prostředku vlastní nebo data](../windows/creating-a-new-custom-or-data-resource.md)  
  
## <a name="managed-resources"></a>Spravované prostředky  
 Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a binární editor pro práci se soubory prostředků v spravované projekty. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Editory prostředků](../windows/resource-editors.md)

