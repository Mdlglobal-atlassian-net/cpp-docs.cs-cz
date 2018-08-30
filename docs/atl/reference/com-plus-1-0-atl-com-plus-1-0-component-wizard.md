---
title: COM + 1.0, Průvodce komponentami ATL COM + 1.0 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.options
dev_langs:
- C++
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 158d279106538fd059252f8e8dcd19aeb6a20f6d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198189"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM + 1.0, Průvodce komponentami ATL COM + 1.0
Na této stránce průvodce komponenta knihovny ATL modelu COM + 1.0 zadat typ rozhraní a další rozhraní, a proto není podporován.  
  
 Další informace o projekty knihovny ATL a třídy knihovny ATL modelu COM, naleznete v tématu [desktopové komponenty ATL COM](../../atl/atl-com-desktop-components.md).  
  
 **Rozhraní**  
 Určuje typ rozhraní, které podporuje objektu. Ve výchozím nastavení podporuje duální rozhraní objektu.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Duální**|Určuje, že objekt podporuje duální rozhraní (jeho vtable má funkce vlastního rozhraní a pozdní vazby `IDispatch` metody). Umožňuje klientům modelu COM a spustila samostatná instance přístup k objektu.|  
|**Vlastní**|Určuje, že objekt podporuje vlastní rozhraní (jeho vtable má vlastní funkce rozhraní). Vlastní rozhraní může být rychlejší než duální rozhraní, zejména přes hranice procesu.<br /><br /> -   **Automatizace kompatibilní** přidává podporu automatizace pro vlastní rozhraní. Pro projekty s atributy, nastaví **oleautomation** atribut v coclass.|  
  
 **Do fronty**  
 Označuje, že klienti mohou volat tuto součást asynchronně pomocí fronty zpráv. Do souboru .h (s atributy projekty) nebo do souboru IDL (bez atributové projekty), přidá komponenty vlastní makro s atributy (TLBATTR_QUEUEABLE, 0).  
  
 **Podpora**  
 Označuje další podporu pro zpracování a objekt řízení chyb.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**ISupportErrorInfo**|Vytvoří podpora [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) rozhraní objektu lze klientovi vrátit informace o chybě.|  
|**IObjectControl v jazyce**|Poskytuje objekt přístup k tři [IObjectControl v jazyce](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectcontrol) metody: [aktivovat](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-activate), [CanBePooled](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled), a [deaktivovat](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate).|  
|**IObjectConstruct**|Vytvoří podpora [IObjectConstruct](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectconstruct) rozhraní pro správu předáním hodnoty parametrů z jiných metod nebo objekty.|  
  
 **Transakce**  
 Označuje, že objekt podporuje transakce. Obsahuje soubor mtxattr v souboru IDL (bez atributové projekty).  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Podporované**|Určuje, zda objekt nikdy kořenové datového proudu transakce přidáním custom(TLBATTR_TRANS_SUPPORTED,0) komponenty atribut – makro do souboru .h (s atributy projekty) nebo do souboru IDL (bez atributové projekty).|  
|**Vyžaduje**|Určuje, že objekt může nebo nemusí být kořenový datového proudu transakce přidáním custom(TLBATTR_TRANS_REQUIRED,0) komponenty atribut – makro do souboru .h (s atributy projekty) nebo do souboru IDL (bez atributové projekty).|  
|**Nepodporuje se**|Určuje, že objekt nezahrnuje transakce. Přidá custom(TLBATTR_TRANS_NOTSUPP,0) komponenty atribut – makro do souboru .h (s atributy projekty) nebo do souboru IDL (bez atributové projekty).|  
|**Požaduje novou**|Určuje, že objekt je vždy kořenový datového proudu transakce přidáním custom(TLBATTR_TRANS_REQNEW,0) komponenty atribut – makro do souboru .h (s atributy projekty) nebo do souboru IDL (bez atributové projekty).|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce komponentami 1.0 knihovny ATL modelu COM +](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [Komponenta knihovny ATL modelu COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

