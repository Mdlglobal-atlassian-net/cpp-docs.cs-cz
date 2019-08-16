---
title: Průvodce komponentami COM+ 1.0, ATL COM+ 1.0
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.mts.options
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
ms.openlocfilehash: 83b7beafe537f6b271b254d16505b515a41acf27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496696"
---
# <a name="com-10-atl-com-10-component-wizard"></a>Průvodce komponentami COM+ 1.0, ATL COM+ 1.0

::: moniker range="vs-2019"

Tento průvodce není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="<=vs-2017"

Pomocí této stránky průvodce komponentami ATL COM+ 1,0 můžete zadat typ rozhraní a další rozhraní, která se mají podporovat.

Další informace o projektech ATL a třídách ATL COM naleznete v tématu [komponenty ATL com Desktop](../../atl/atl-com-desktop-components.md).

- **Rozhraní**

   Určuje typ rozhraní, které objekt podporuje. Ve výchozím nastavení objekt podporuje duální rozhraní.

   |Možnost|Popis|
   |------------|-----------------|
   |**Možnost**|Určuje, že objekt podporuje duální rozhraní (jeho vtable má funkce vlastního rozhraní a metody pozdní vazby `IDispatch` ). Umožňuje klientům modelu COM a Automatizačním řadičům přístup k objektu.|
   |**Vlastní**|Určuje, že objekt podporuje vlastní rozhraní (jeho vtable má funkce vlastního rozhraní). Vlastní rozhraní může být rychlejší než duální rozhraní, zejména napříč hranicemi procesů.<br /><br /> - **Kompatibilní** s automatizací Přidá podporu automatizace do vlastního rozhraní. U atributových projektů nastaví atribut **oleautomation** v coclass.|

- **Ve frontě**

   Označuje, že klienti mohou tuto komponentu asynchronně volat pomocí front zpráv. Přidá vlastní makro s atributy (TLBATTR_QUEUEABLE, 0) do souboru. h (atributy projektů) nebo souboru. IDL (neatributové projekty).

- **Podpora**

   Označuje další podporu pro zpracování chyb a řízení objektů.

   |Možnost|Popis|
   |------------|-----------------|
   |**ISupportErrorInfo**|Vytvoří podporu pro rozhraní [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) , aby mohl objekt vracet informace o chybách klientovi.|
   |**IObjectControl**|Poskytuje vašemu objektu přístup k třem metodám [IObjectControl](/windows/win32/api/comsvcs/nn-comsvcs-iobjectcontrol) : [Aktivujte](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-activate), [CanBePooled](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled)a deaktivujte. [](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate)|
   |**IObjectConstruct**|Vytvoří podporu pro rozhraní [IObjectConstruct](/windows/win32/api/comsvcs/nn-comsvcs-iobjectconstruct) ke správě předávání parametrů z jiných metod nebo objektů.|

- **Transakce**

   Označuje, že objekt podporuje transakce. Obsahuje soubor mtxattr. h v souboru. IDL (neatributové projekty).

   |Možnost|Popis|
   |------------|-----------------|
   |**Podporuje se**|Určuje, že objekt není nikdy kořenem transakčního datového proudu tím, že přidáte vlastní makro atributu komponenty (TLBATTR_TRANS_SUPPORTED, 0) do souboru. h (atributy Projects) nebo do souboru. IDL (neatributové projekty).|
   |**Požadováno**|Určuje, že objekt může nebo nemusí být kořenem transakčního datového proudu přidáním atributu komponenty vlastní (TLBATTR_TRANS_REQUIRED, 0) do souboru. h (s atributy projekty) nebo do souboru. IDL (neatributové projekty).|
   |**Nepodporuje se**|Určuje, že objekt vyloučí transakce. Přidá vlastní makro atributu komponenty (TLBATTR_TRANS_NOTSUPP, 0) do souboru. h (atributy projektů) nebo do souboru. IDL (neatributové projekty).|
   |**Vyžaduje nové**|Určuje, že objekt je vždy kořenem transakčního datového proudu přidáním atributu komponenty vlastní (TLBATTR_TRANS_REQNEW, 0) do souboru. h (atributové projekty) nebo do souboru. IDL (neatributové projekty).|

::: moniker-end

## <a name="see-also"></a>Viz také:

[Průvodce komponentami ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[Komponenta ATL COM+ 1,0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
