---
title: CBitmapButton – třída
ms.date: 11/04/2016
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
ms.openlocfilehash: df21591dec1da5861125d7e9480fb9345aaad061
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752945"
---
# <a name="cbitmapbutton-class"></a>CBitmapButton – třída

Vytvoří ovládací prvky pro stisknutí tlačítka označené bitem namapovanými obrázky místo textu.

## <a name="syntax"></a>Syntaxe

```
class CBitmapButton : public CButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Vytvoří `CBitmapButton` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CBitmapButton::Automatické načtení](#autoload)|Přidruží tlačítko v dialogovém okně `CBitmapButton` k objektu třídy, načte bitmapy podle názvu a zvětší tlačítko tak, aby se vešel do bitmapy.|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Inicializuje objekt načtením jednoho nebo více pojmenovaných bitmapových prostředků ze souboru prostředků aplikace a připojením bitmap k objektu.|
|[CBitmapButton::SizeToContent](#sizetocontent)|Změní velikost tlačítka tak, aby vyhovovalo bitmapě.|

## <a name="remarks"></a>Poznámky

`CBitmapButton`objekty obsahují až čtyři bitmapy, které obsahují obrazy pro různé stavy, které může tlačítko předpokládat: nahoru (nebo normální), dolů (nebo vybrané), zaostřené a zakázané. Je vyžadována pouze první bitmapa; ostatní jsou volitelné.

Bitmapové tlačítko obrázky obsahují ohraničení kolem obrazu, stejně jako obraz sám. Ohraničení obvykle hraje roli při zobrazování stavu tlačítka. Například bitmapa pro zaostřený stav je obvykle jako ta pro stav nahoru, ale s přerušovaným obdélníkem vsazeným z ohraničení nebo tlustou plnou čárou na okraji. Bitmapa zakázaného stavu se obvykle podobá tichu pro stav nahoru, ale má nižší kontrast (například šedě nebo šedě).

Tyto rastrové obrázky mohou mít libovolnou velikost, ale všechny jsou považovány za stejně velké jako rastrový obrázek pro stav nahoru.

Různé aplikace vyžadují různé kombinace bitmapových obrazů:

|Nahoru|Dolů|Focused|Zakázáno|Aplikace|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmapové|
|×|×|||Tlačítko bez WS_TABSTOP stylu|
|×|×|×|×|Dialogové tlačítko se všemi stavy|
|×|×|×||Dialogové tlačítko se stylem WS_TABSTOP|

Při vytváření ovládacího prvku bitmapové tlačítko nastavte styl BS_OWNERDRAW, který určuje, že tlačítko je nakresleno vlastníkem. To způsobí, že systém Windows odeslat WM_MEASUREITEM a WM_DRAWITEM zprávy pro tlačítko; rozhraní framework zpracovává tyto zprávy a spravuje vzhled tlačítka za vás.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Vytvoření ovládacího prvku bitmapového tlačítka v klientské oblasti okna

1. Vytvořte pro tlačítko jeden až čtyři bitmapové obrazy.

1. Vytvořte objekt [CBitmapButton.](#cbitmapbutton)

1. Voláním funkce [Vytvořit](../../mfc/reference/cbutton-class.md#create) vytvořte ovládací prvek tlačítka `CBitmapButton` Systému Windows a připojte jej k objektu.

1. Volání členské funkce [LoadBitmaps](#loadbitmaps) k načtení bitmapových prostředků po vytvoření bitmapového tlačítka.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Zahrnutí ovládacího prvku bitmapového tlačítka do dialogového okna

1. Vytvořte pro tlačítko jeden až čtyři bitmapové obrazy.

1. Vytvořte šablonu dialogu s tlačítkem kreslení vlastníka umístěným tam, kde chcete bitmapové tlačítko. Na velikosti tlačítka v šabloně nezáleží.

1. Nastavte titulek tlačítka na hodnotu, jako je například "MYIMAGE" a definujte symbol pro tlačítko, jako je IDC_MYIMAGE.

1. Ve skriptu prostředků aplikace přiřaďte každému z obrázků vytvořených pro tlačítko ID vytvořené připojením jednoho z písmen "U", "D", "F" nebo "X" (pro nahoru, dolů, zaostřené a zakázané) k řetězci použitému pro titulek tlačítka v kroku 3. Pro titulek tlačítka "MYIMAGE", například ID by "MYIMAGEU", "MYIMAGED", "MYIMAGEF" a "MYIMAGEX." Je **nutné** zadat ID rastrových obrázků v rámci dvojitých uvozovek. V opačném případě editor prostředků přiřadí prostředek celé číslo a knihovna MFC se nezdaří při načítání bitové kopie.

1. Do třídy dialogů aplikace (odvozené z ) `CDialog`přidejte `CBitmapButton` členský objekt.

1. V `CDialog` rutině [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) objektu `CBitmapButton` volejte funkci [automatického načtení](#autoload) objektu pomocí jako parametry `CDialog` ID ovládacího prvku tlačítka a **ukazatele tohoto** objektu.

Pokud chcete zpracovávat zprávy oznámení systému Windows, například BN_CLICKED, odeslané ovládacím prvkem `CDialog`bitmapového `CDialog`tlačítka jeho nadřazené (obvykle třída odvozená z ), přidejte do objektu -derived položku položky mapy zprávy a členské funkce obslužné rutiny zprávy pro každou zprávu. Oznámení odeslaná objektem `CBitmapButton` jsou stejná jako oznámení odeslaná objektem [CButton.](../../mfc/reference/cbutton-class.md)

Třída [CToolBar](../../mfc/reference/ctoolbar-class.md) má jiný přístup k bitmapových tlačítek.

Další informace `CBitmapButton`naleznete v tématu [Controls](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a>CBitmapButton::Automatické načtení

Přidruží tlačítko v dialogovém okně `CBitmapButton` k objektu třídy, načte bitmapy podle názvu a zvětší tlačítko tak, aby se vešel do bitmapy.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
ID ovládacího prvku tlačítka.

*pParent*<br/>
Ukazatel na objekt, který je vlastní tlačítko.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pomocí `AutoLoad` této funkce můžete inicializovat tlačítko kreslení vlastníka v dialogovém okně jako bitmapové tlačítko. Pokyny pro použití této funkce jsou `CBitmapButton` v poznámkách pro třídu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton

Vytvoří `CBitmapButton` objekt.

```
CBitmapButton();
```

### <a name="remarks"></a>Poznámky

Po vytvoření objektu `CBitmapButton` C++ volejte [CButton::Create](../../mfc/reference/cbutton-class.md#create) a vytvořte ovládací `CBitmapButton` prvek tlačítka systému Windows a připojte jej k objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a>CBitmapButton::LoadBitmaps

Tuto funkci použijte, pokud chcete načíst bitmapové obrazy identifikované jejich názvy `AutoLoad` prostředků nebo čísly ID, nebo pokud tuto funkci nemůžete použít, protože například vytváříte bitmapové tlačítko, které není součástí dialogového okna.

```
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,
    LPCTSTR lpszBitmapResourceSel = NULL,
    LPCTSTR lpszBitmapResourceFocus = NULL,
    LPCTSTR lpszBitmapResourceDisabled = NULL);

BOOL LoadBitmaps(
    UINT nIDBitmapResource,
    UINT nIDBitmapResourceSel = 0,
    UINT nIDBitmapResourceFocus = 0,
    UINT nIDBitmapResourceDisabled = 0);
```

### <a name="parameters"></a>Parametry

*lpszBitmapZdroj*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje název bitmapy pro normální stav nebo stav "nahoru" bitmapového tlačítka. Povinná hodnota.

*lpszBitmapResourceSel*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje název bitmapy pro vybraný nebo "dolů" stav bitmapového tlačítka. Může být null.

*lpszBitmapResourceFocus*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje název bitmapy pro stav zaměření bitmapového tlačítka. Může být null.

*lpszBitmapResourceDisabled*<br/>
Odkazuje na řetězec ukončený hodnotou null, který obsahuje název rastrového bodu pro zakázaný stav bitmapového tlačítka. Může být null.

*nIDBitmapResource*<br/>
Určuje číslo ID prostředku prostředku bitmapy pro normální nebo "nahoru" stav bitmapového tlačítka. Povinná hodnota.

*nIDBitmapResourceSel*<br/>
Určuje číslo ID prostředku bitmapového prostředku pro vybraný nebo vypnutý stav bitmapového tlačítka. Může být 0.

*nIDBitmapResourceFocus*<br/>
Určuje číslo ID prostředku prostředku bitmapy pro stav zaměření bitmapového tlačítka. Může být 0.

*nIDBitmapResourceDisabled*<br/>
Určuje číslo ID prostředku prostředku bitmapy pro zakázaný stav bitmapového tlačítka. Může být 0.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a>CBitmapButton::SizeToContent

Voláním této funkce změníte velikost bitmapového tlačítka na velikost bitmapy.

```cpp
void SizeToContent();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
