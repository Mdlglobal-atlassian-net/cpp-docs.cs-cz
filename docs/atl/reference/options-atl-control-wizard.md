---
title: Možnosti, Průvodce ovládacím prvkem ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 1dd136739162c72d8064deb9b1498794f1985e1b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282978"
---
# <a name="options-atl-control-wizard"></a>Možnosti, Průvodce ovládacím prvkem ATL

Pomocí této stránky v průvodci můžete definovat typ ovládacího prvku, který vytváříte a úroveň podpory rozhraní, které obsahuje.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

### <a name="control-type"></a>Typ ovládacího prvku

Druh ovládacího prvku, který chcete vytvořit.

- **Standardní ovládací prvek**: Ovládací prvek ActiveX.

- **Složený ovládací prvek**: Ovládací prvek ActiveX, který může obsahovat (podobně jako do dialogového okna) jiné ovládací prvky ActiveX nebo ovládací prvky Windows. Složený ovládací prvek obsahuje následující:

  - Šablona pro dialogové okno, které implementuje složeného ovládacího prvku.

  - Vlastní prostředek REGISTRU, který automaticky registruje složeného ovládacího prvku při vyvolání.

  - Třída C++, který implementuje složeného ovládacího prvku.

  - Rozhraní modelu COM, vystavené složeného ovládacího prvku.

  - Zkušební stránku HTML obsahující složeného ovládacího prvku.

    Ve výchozím nastavení, nastaví tento ovládací prvek [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) na hodnotu true označuje, že se jedná o ovládacího prvku v okně. Implementuje mapu jímky. Další informace najdete v tématu [podporu pro ovládací prvek DHTML](../../atl/atl-support-for-dhtml-controls.md).

- **Ovládací prvek DHTML**: Ovládacího prvku ATL DHTML určuje uživatelského rozhraní pomocí jazyka HTML. Třída DHTML uživatelského rozhraní obsahuje mapu COM. Ve výchozím nastavení, nastaví tento ovládací prvek [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) na hodnotu true označuje, že se jedná o ovládacího prvku v okně.

   Další informace najdete v tématu [identifikace prvků projektu ovládací prvek DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).

### <a name="minimal-control"></a>Minimální ovládací prvek

Podporuje pouze rozhraní, která je to nezbytně nutné většina kontejneru. Můžete nastavit **minimální ovládací prvek** pro všechny typy ovládacích prvků: můžete vytvořit minimální standardního ovládacího prvku, minimální složeného ovládacího prvku nebo minimální ovládací prvek DHTML.

### <a name="aggregation"></a>Aggregation

Přidá podporu agregace pro ovládací prvek, který vytváříte. Další informace najdete v tématu [agregace](../../atl/aggregation.md).

- **Ano**: Vytvoření ovládacího prvku, který se dají agregovat.

- **Ne**: Vytvoření ovládacího prvku, který nemůže být agregován.

- **Pouze**: Vytvoření ovládacího prvku, který může být vytvořena pouze prostřednictvím agregace.

### <a name="threading-model"></a>Model vláken

Určuje, že model vláken použit v ovládacím prvku.

- **Jeden**: Ovládací prvek se spustí pouze v primárním vláknu COM.

- **Apartment**: Ovládací prvek lze vytvořit v libovolné objektu apartment pro jedno vlákno. Výchozí nastavení

### <a name="interface"></a>Rozhraní

Typ rozhraní, které zpřístupní tento ovládací prvek do kontejneru.

- **Duální**: Vytvoří rozhraní, které zveřejňuje vlastnosti a metody prostřednictvím `IDispatch` a přímo přes VTBL.

- **Vlastní**: Vytvoří rozhraní, které zveřejňuje metody přímo prostřednictvím VTBL.

   Pokud vyberete **vlastní**, můžete zadat, že je ovládací prvek **automatizace kompatibilní**. Pokud vyberete **automatizace kompatibilní**, přidá průvodce [oleautomation](../../windows/oleautomation.md) atribut rozhraní IDL, a rozhraní může být zařazována univerzální zařazováním v oleaut32.dll. Zobrazit [Podrobnosti zařazování](/windows/desktop/com/marshaling-details) v sadě Windows SDK pro další informace.

   Kromě toho pokud vyberete **automatizace kompatibilní**, pak všechny parametry pro všechny metody v ovládacím prvku musí být typu VARIANT kompatibilní.

### <a name="support"></a>Podpora

Nastaví další různé podporu pro ovládací prvek.

- **Body připojení**: Umožňuje spojovací body pro svůj objekt tím, že jsou odvozeny z třídy objektu [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) a díky kterému jej k vystavení zdrojové rozhraní.

- **Licenci**: Přidá do ovládacího prvku pro podporu [licencování](/windows/desktop/com/licensing). Licencované ovládací prvky je možné hostovat, pouze pokud klientský počítač nemá správnou licenci.

## <a name="see-also"></a>Viz také:

[Průvodce ovládacími prvky ATL](../../atl/reference/atl-control-wizard.md)
