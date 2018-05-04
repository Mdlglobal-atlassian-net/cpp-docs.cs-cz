---
title: Implementace stránky vlastností | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1db6ca4ea374cd76d5b0e1df8e6c0cd03474fdf2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-property-pages"></a>Implementace stránky vlastností
Stránky vlastností jsou, které implementují objekty COM `IPropertyPage` nebo **IPropertyPage2** rozhraní. ATL poskytuje podporu pro implementaci stránky vlastností prostřednictvím [ATL vlastnost stránky průvodce](../atl/reference/atl-property-page-wizard.md) v [dialogové okno Přidat třídu](../ide/add-class-dialog-box.md).  
  
 Pokud chcete vytvořit pomocí knihovny ATL stránky vlastností:  
  
-   Vytvoření nebo otevření projektu knihovny ATL dynamická knihovna (DLL) serveru.  
  
-   Otevřete [dialogové okno Přidat třídu](../ide/add-class-dialog-box.md) a vyberte **ATL – stránky vlastností**.  
  
-   Zajistěte, aby byl stránky vlastností objektu apartment zařazování (protože má uživatelské rozhraní).  
  
-   Nastavte název, popis (Doc String) a soubor nápovědy, který se má přidružit stránku.  
  
-   Přidání ovládacích prvků do prostředku generovaného dialogového okna tak, aby fungoval jako uživatelského rozhraní stránky vlastností.  
  
-   Odpověď na změny v uživatelském rozhraní vaší stránky provést ověření, aktualizujte stránku lokalitu nebo aktualizovat objekty přidružené k vaší stránky. Konkrétně volání [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) když uživatel provede změny na stránku vlastností.  
  
-   Volitelně můžete přepsat `IPropertyPageImpl` metod pomocí níže uvedených pokynů.  
  
    |IPropertyPageImpl – metoda|Přepsání, pokud chcete...|Poznámky|  
    |------------------------------|----------------------------------|-----------|  
    |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Proveďte kontrolu základní vhodnosti na počet objektů, které jsou předávány na stránku a rozhraní, které podporují.|Provést vlastní kód před voláním implementaci základní třídy. Pokud probíhá nastavení objekty nevyhovují vašim očekáváním, má volání selhat co nejdříve.|  
    |[Aktivovat](../atl/reference/ipropertypageimpl-class.md#activate)|Inicializujte vaší stránky uživatelské rozhraní (například nastavit ovládací prvky dialogového okna s aktuální hodnoty vlastností z objektů, ovládací prvky vytvořit dynamicky nebo provádět jiné inicializacích).|Volejte základní třída implementaci před kódu, takže základní třídy možnost vytvoření dialogového okna a všechny ovládací prvky, než se pokusíte je aktualizovat.|  
    |[Použít](../atl/reference/ipropertypageimpl-class.md#apply)|Ověřte nastavení vlastností a aktualizovat objekty.|Není nutné volat implementaci základní třídy, protože nedělá nic kromě trasování volání.|  
    |[Deaktivace](../atl/reference/ipropertypageimpl-class.md#deactivate)|Vymazat všechny položky související s okno.|Základní třída implementace zničí dialogu představující stránku vlastností. Pokud potřebujete vyčištění zničen dialogové okno, měli byste přidat kód před voláním základní třídy.|  
  
 Příklad implementace vlastností stránky, najdete v části [příklad: implementace stránky vlastností](../atl/example-implementing-a-property-page.md).  
  
> [!NOTE]
>  Pokud chcete v stránky vlastností hostitelské ovládací prvky ActiveX, musíte změnit odvození vaší třídy generované v průvodci. Nahraďte **CDialogImpl\<CYourClass >** s **CAxDialogImpl\<CYourClass >** v seznamu základní třídy.  
  
## <a name="see-also"></a>Viz také  
 [Stránky vlastností](../atl/atl-com-property-pages.md)   
 [Ukázka ATLPages](../visual-cpp-samples.md)

