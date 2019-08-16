---
title: Možnosti, Průvodce ovládacím prvkem ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 25db3995687011de5e9cc0a98506cd26f2f1af0b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495444"
---
# <a name="options-atl-control-wizard"></a>Možnosti, Průvodce ovládacím prvkem ATL

Pomocí této stránky průvodce můžete definovat typ ovládacího prvku, který vytváříte, a úroveň podpory rozhraní, kterou obsahuje.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

### <a name="control-type"></a>Typ ovládacího prvku

Typ ovládacího prvku, který chcete vytvořit.

- **Standardní ovládací prvek**: Ovládací prvek ActiveX.

- **Složený ovládací prvek**: Ovládací prvek ActiveX, který může obsahovat (podobně jako dialogové okno) jiné ovládací prvky ActiveX nebo ovládací prvky systému Windows. Složený ovládací prvek zahrnuje následující:

  - Šablona pro dialogové okno, které implementuje složený ovládací prvek.

  - Vlastní prostředek, registr, který při vyvolání automaticky zaregistruje složený ovládací prvek.

  - C++ Třída, která implementuje složený ovládací prvek.

  - Rozhraní modelu COM vystavené složeným ovládacím prvkem.

  - Zkušební stránka HTML obsahující složený ovládací prvek.

    Ve výchozím nastavení tento ovládací prvek nastaví [CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) na hodnotu true, aby označoval, že se jedná o ovládací prvek v okně. Implementuje mapu jímky. Další informace najdete v tématu [Podpora ovládacího prvku DHTML](../../atl/atl-support-for-dhtml-controls.md).

- **Ovládací prvek DHTML**: Ovládací prvek ATL DHTML Určuje uživatelské rozhraní pomocí jazyka HTML. Třída uživatelského rozhraní DHTML obsahuje mapu modelu COM. Ve výchozím nastavení tento ovládací prvek nastaví [CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) na hodnotu true, aby označoval, že se jedná o ovládací prvek v okně.

   Další informace naleznete v tématu [určení prvků projektu ovládacího prvku DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).

### <a name="minimal-control"></a>Minimální ovládací prvek

Podporuje pouze rozhraní, která jsou naprosto potřebná pro většinu kontejnerů. Můžete nastavit **minimální kontrolu** pro libovolný typ ovládacího prvku: můžete vytvořit minimální standardní ovládací prvek, minimální složený ovládací prvek nebo minimální ovládací prvek DHTML.

### <a name="aggregation"></a>Agregace

Přidá podporu agregace pro ovládací prvek, který vytváříte. Další informace naleznete v tématu [agregace](../../atl/aggregation.md).

- **Ano**: Vytvoří ovládací prvek, který lze agregovat.

- **Ne**: Vytvoří ovládací prvek, který nelze agregovat.

- **Jenom**: Vytvoří ovládací prvek, který lze vytvořit pouze pomocí agregace.

### <a name="threading-model"></a>Model vláken

Určuje, že model vláken používaný ovládacím prvkem.

- **Jedna**: Ovládací prvek bude spuštěn pouze v primárním vlákně COM.

- **Byt**: Ovládací prvek lze vytvořit v jakémkoli vlákně typu apartment. Výchozí nastavení

### <a name="interface"></a>Rozhraní

Typ rozhraní, které tento ovládací prvek zpřístupňuje kontejneru.

- **Duální**: Vytvoří rozhraní, které zpřístupňuje vlastnosti a metody `IDispatch` prostřednictvím a přímo přes VTBL.

- **Vlastní**: Vytvoří rozhraní, které zveřejňuje metody přímo přes VTBL.

   Pokud vyberete možnost **vlastní**, můžete určit, že je ovládací prvek **kompatibilní**s automatizací. Pokud vyberete možnost **kompatibilní**s automatizací, Průvodce přidá atribut [oleautomation](../../windows/oleautomation.md) do rozhraní v IDL a rozhraní může být zařazeno do univerzálního zařazovacího modulu v Oleaut32. dll. Další informace najdete v tématu informace [o zařazování](/windows/win32/com/marshaling-details) v Windows SDK.

   Pokud navíc vyberete možnost **Automatizace kompatibilní**, pak všechny parametry pro všechny metody v ovládacím prvku musí být kompatibilní s variantou.

### <a name="support"></a>Podpora

Nastaví další různé podpory pro ovládací prvek.

- **Body připojení**: Umožňuje spojovací body pro váš objekt tím, že třídu objektu je odvozen z [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) a umožňuje vystavit zdrojové rozhraní.

- **Licencovaná**: Přidá podporu k ovládacímu prvku [](/windows/win32/com/licensing)pro licencování. Licencované ovládací prvky lze hostovat pouze v případě, že má klientský počítač správnou licenci.

## <a name="see-also"></a>Viz také:

[Průvodce ovládacími prvky ATL](../../atl/reference/atl-control-wizard.md)
