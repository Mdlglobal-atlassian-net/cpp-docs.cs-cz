---
title: COM + 1.0, Průvodce komponentami ATL COM + 1.0
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.mts.options
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
ms.openlocfilehash: 0fa649ba41a684be6ed18bd05d48954503c5db16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278589"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM + 1.0, Průvodce komponentami ATL COM + 1.0

Na této stránce průvodce komponenta knihovny ATL modelu COM + 1.0 zadat typ rozhraní a další rozhraní, a proto není podporován.

Další informace o projekty knihovny ATL a třídy knihovny ATL modelu COM, naleznete v tématu [desktopové komponenty ATL COM](../../atl/atl-com-desktop-components.md).

- **Rozhraní**

   Určuje typ rozhraní, které podporuje objektu. Ve výchozím nastavení podporuje duální rozhraní objektu.

   |Možnost|Popis|
   |------------|-----------------|
   |**Duální**|Určuje, že objekt podporuje duální rozhraní (jeho vtable má funkce vlastního rozhraní a pozdní vazby `IDispatch` metody). Umožňuje klientům modelu COM a spustila samostatná instance přístup k objektu.|
   |**Vlastní**|Určuje, že objekt podporuje vlastní rozhraní (jeho vtable má vlastní funkce rozhraní). Vlastní rozhraní může být rychlejší než duální rozhraní, zejména přes hranice procesu.<br /><br /> - **Automatizace kompatibilní** přidává podporu automatizace pro vlastní rozhraní. Pro projekty s atributy, nastaví **oleautomation** atribut v coclass.|

- **Do fronty**

   Označuje, že klienti mohou volat tuto součást asynchronně pomocí fronty zpráv. Do souboru .h (s atributy projekty) nebo do souboru IDL (bez atributové projekty), přidá komponenty vlastní makro s atributy (TLBATTR_QUEUEABLE, 0).

- **Podpora**

   Označuje další podporu pro zpracování a objekt řízení chyb.

   |Možnost|Popis|
   |------------|-----------------|
   |**ISupportErrorInfo**|Vytvoří podpora [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) rozhraní objektu lze klientovi vrátit informace o chybě.|
   |**IObjectControl**|Poskytuje objekt přístup k tři [IObjectControl v jazyce](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectcontrol) metody: [Aktivovat](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-activate), [CanBePooled](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled), a [deaktivovat](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate).|
   |**IObjectConstruct**|Vytvoří podpora [IObjectConstruct](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectconstruct) rozhraní pro správu předáním hodnoty parametrů z jiných metod nebo objekty.|

- **Transakce**

   Označuje, že objekt podporuje transakce. Obsahuje soubor mtxattr v souboru IDL (bez atributové projekty).

   |Možnost|Popis|
   |------------|-----------------|
   |**Podporuje se**|Určuje, zda objekt nikdy kořenové datového proudu transakce přidáním custom(TLBATTR_TRANS_SUPPORTED,0) komponenty atribut – makro do souboru .h (s atributy projekty) nebo do souboru IDL (bez atributové projekty).|
   |**Požadováno**|Určuje, že objekt může nebo nemusí být kořenový datového proudu transakce přidáním custom(TLBATTR_TRANS_REQUIRED,0) komponenty atribut – makro do souboru .h (s atributy projekty) nebo do souboru IDL (bez atributové projekty).|
   |**Nepodporuje se**|Určuje, že objekt nezahrnuje transakce. Přidá custom(TLBATTR_TRANS_NOTSUPP,0) komponenty atribut – makro do souboru .h (s atributy projekty) nebo do souboru IDL (bez atributové projekty).|
   |**Požaduje novou**|Určuje, že objekt je vždy kořenový datového proudu transakce přidáním custom(TLBATTR_TRANS_REQNEW,0) komponenty atribut – makro do souboru .h (s atributy projekty) nebo do souboru IDL (bez atributové projekty).|

## <a name="see-also"></a>Viz také:

[Průvodce komponentami ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[Komponenta knihovny ATL modelu COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
