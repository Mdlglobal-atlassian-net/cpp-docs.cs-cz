---
title: "Symboly: Identifikátory prostředků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.symbol.identifiers
dev_langs:
- C++
helpviewer_keywords:
- symbols, resource identifiers
- symbols, creating
- resource symbols
- symbols, editing
- resource editors, resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 931ec9cb5d7e756d47a24c0c2b30b8686cd0fd4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="symbols-resource-identifiers"></a>Symboly: identifikátory prostředků
Symbol je resource identifier (ID), která se skládá ze dvou částí: textový řetězec (názvu symbolu) namapované na celočíselnou hodnotu (symbol hodnota). Příklad:  
  
```  
IDC_EDITNAME = 5100  
```  
  
 Názvy symbolů jsou nejčastěji označovány jako identifikátory.  
  
 Symboly zadejte popisný způsob odkazující na prostředky a objekty uživatelského rozhraní, ve zdrojovém kódu a při práci s nimi v editory prostředků. Můžete zobrazit a upravit symboly v jedné pomocí vhodné místo [symboly prostředků – dialogové okno](../windows/viewing-resource-symbols.md).  
  
 Když vytvoříte nový prostředek nebo objektu prostředků [editory prostředků](../windows/resource-editors.md) zadejte výchozí název prostředku, například `IDC_RADIO1`a přiřadit hodnotu. Definice name plus hodnota je uložena v souboru Resource.h.  
  
> [!NOTE]
>  Když kopírujete prostředky nebo objektů prostředků z jednoho .rc souboru do druhého, Visual C++ změnit přenášená prostředků symbol hodnotu, nebo názvu symbolu a hodnotu, aby nedocházelo ke konfliktům s názvy symbolů nebo hodnoty ve stávající soubor.  
  
 S růstem vaší aplikace v velikosti a vyspělosti proto nemá počet prostředků a symboly. Sledování velkého počtu symboly na různých místech několik souborů může být obtížné. [Symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md) zjednodušuje správu symbol tím, že nabízí centrální nástroj, pomocí kterého můžete:  
  
- [Symboly prostředků zobrazení](../windows/viewing-resource-symbols.md)  
  
- [Vytváření nových symbolů](../windows/creating-new-symbols.md)  
  
- [Změna nepřiřazených symbolů](../windows/changing-unassigned-symbols.md)  
  
- [Odstranění nepřiřazených symbolů](../windows/deleting-unassigned-symbols.md)  
  
- [Otevření editoru prostředků pro daný Symbol](../windows/opening-the-resource-editor-for-a-given-symbol.md)  
  
- [Změna symbolu nebo názvu symbolu (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)  
  
- [Změna číselné hodnoty symbolu](../windows/changing-a-symbol-s-numeric-value.md)  
  
- [Změna názvů hlavičkových souborů symbolu](../windows/changing-the-names-of-symbol-header-files.md)  
  
- [Zahrnout sdílených (jen pro čtení) nebo vypočtených symbolů](../windows/including-shared-read-only-or-calculated-symbols.md)  
  
- [Zobrazit ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vyhledávání symbolů v prostředcích](../windows/how-to-search-for-symbols-in-resources.md)   
 [Editory prostředků](../windows/resource-editors.md)   
 [Soubory prostředků](../windows/resource-files-visual-studio.md)

