---
title: "Modelu COM + 1.0, Průvodce součástmi ATL COM + 1.0 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.options
dev_langs:
- C++
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 102e6a0a9b7055000d051f5fb729dd45863a16cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="com-10-atl-com-10-component-wizard"></a>Modelu COM + 1.0, Průvodce součástmi ATL COM + 1.0
Na této stránce Průvodce komponentou ATL COM + 1.0 určit typ rozhraní a další rozhraní, které mají být podporovány.  
  
 Další informace o projekty knihovny ATL a třídy ATL COM, najdete v části [ATL COM – součásti plochy](../../atl/atl-com-desktop-components.md).  
  
 **Rozhraní**  
 Určuje typ rozhraní, které podporuje objekt. Ve výchozím nastavení podporuje objekt duální rozhraní.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Duální**|Určuje, že objekt podporuje rozhraní dual (jeho vtable má funkce vlastního rozhraní a pozdní vazba `IDispatch` metody). Umožňuje klientům modelu COM a automatizace řadiče přistupovat k tomuto objektu.|  
|**Vlastní**|Určuje, že objekt podporuje vlastní rozhraní (jeho vtable má funkce vlastního rozhraní). Vlastní rozhraní může být rychlejší než duální rozhraní, zejména přes hranice procesu.<br /><br /> -   **Automatizace kompatibilní** přidává podporu automatizace na vlastní rozhraní. S atributy projekty, nastaví **oleautomation** atribut v coclass.|  
  
 **Do fronty**  
 Označuje, že klienti mohou volat tuto komponentu asynchronně pomocí fronty zpráv. Přidá komponenty vlastní makro s atributy (TLBATTR_QUEUEABLE, 0) do souboru h (s atributy projekty) nebo do souboru IDL (neoznačené atributy projekty).  
  
 **Podpora**  
 Označuje další podporu pro zpracování a objekt řízení chyb.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**ISupportErrorInfo**|Vytvoří podporu pro [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) rozhraní tak objekt může vrátit informace o chybě do klienta.|  
|**IObjectControl v jazyce**|Poskytuje objektu přístup do tří [IObjectControl v jazyce](http://msdn.microsoft.com/library/windows/desktop/ms686474) metody: [aktivovat](http://msdn.microsoft.com/library/windows/desktop/ms681303), [CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322), a [deaktivovat](http://msdn.microsoft.com/library/windows/desktop/ms687094).|  
|**IObjectConstruct**|Vytvoří podporu pro [IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583) rozhraní pro správu předávání v parametrech z jiných metod nebo objekty.|  
  
 **Transakce**  
 Označuje, že objekt podporuje transakce. Obsahuje soubor mtxattr v souboru IDL (neoznačené atributy projekty).  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Podporované**|Určuje, že objekt je nikdy kořen datového proudu transakce přidáním custom(TLBATTR_TRANS_SUPPORTED,0) součást atribut makro do souboru h (s atributy projekty) nebo do souboru IDL (neoznačené atributy projekty).|  
|**Požadované**|Určuje, že objekt může nebo nemusí být kořen datového proudu transakce přidáním custom(TLBATTR_TRANS_REQUIRED,0) součást atribut makro do souboru h (s atributy projekty) nebo do souboru IDL (neoznačené atributy projekty).|  
|**Nepodporuje se**|Určuje, že objekt nezahrnuje transakce. Přidá custom(TLBATTR_TRANS_NOTSUPP,0) součást atribut makro do souboru h (s atributy projekty) nebo do souboru IDL (neoznačené atributy projekty).|  
|**Vyžaduje nové**|Určuje, že objekt je vždy kořen datového proudu transakce přidáním custom(TLBATTR_TRANS_REQNEW,0) součást atribut makro do souboru h (s atributy projekty) nebo do souboru IDL (neoznačené atributy projekty).|  
  
## <a name="see-also"></a>Viz také  
 [ATL COM + 1.0 součást Průvodce](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [Komponenta knihovny ATL COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

