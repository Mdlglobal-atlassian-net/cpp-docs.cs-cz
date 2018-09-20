---
title: Cbitmapbutton – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
dev_langs:
- C++
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a4cc427459036b4b124573f47c71146eafcb970
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422253"
---
# <a name="cbitmapbutton-class"></a>Cbitmapbutton – třída

Vytvoří kontrolní prvky stisknutelných tlačítek označené rastrovými obrázky místo textu.

## <a name="syntax"></a>Syntaxe

```
class CBitmapButton : public CButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Vytvoří `CBitmapButton` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CBitmapButton::AutoLoad](#autoload)|Přidruží tlačítko v dialogovém okně objektu `CBitmapButton` třídy, načte bitmap(s) podle názvu a velikosti tlačítko Přizpůsobit rastrový obrázek.|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Inicializuje objekt načtením jeden nebo více prostředků pojmenovaných rastrový obrázek ze souboru prostředků aplikace a připojení rastrové obrázky do objektu.|
|[CBitmapButton::SizeToContent](#sizetocontent)|Velikost tlačítka podle rastrového obrázku.|

## <a name="remarks"></a>Poznámky

`CBitmapButton` objekty obsahují až čtyři rastrové obrázky, které obsahují Image pro různé stavy tlačítka můžete předpokládat: nahoru (nebo normální), dolů (nebo vybraných), zaměřuje a zakázané. Pouze první rastrového obrázku je vyžadováno. ostatní jsou volitelné.

Tlačítko s rastrovým Image zahrnují ohraničení kolem obrázku, jakož i samotný obrázek. Ohraničení obvykle hraje část v zobrazení stav tlačítka. Například rastrového obrázku pro cílené stav je obvykle třeba jednoho pro aktuálním stavu, ale s inset obdélník přerušované ohraničení nebo silný plnou čáru na hranicích. Rastrový obrázek pro zakázané stavu obvykle následujícímu aktuálním stavu, ale má nižší kontrastu (podobný výběr neaktivní nebo šedým nabídky).

Tyto bitmapy může mít libovolnou velikost, ale všechny zacházeno, jako by byly stejné velikosti jako rastrový obrázek pro aktuálním stavu.

Různé aplikace vyžadují různé kombinace bitmapové obrázky:

|Nahoru|Dolů|Fokus|Zakázané|Aplikace|
|--------|----------|-------------|--------------|-----------------|
|×||||Rastrový obrázek|
|×|×|||Tlačítka bez textu WS_TABSTOP styl|
|×|×|×|×|Dialogové okno tlačítko s všechny stavy|
|×|×|×||Dialogové okno tlačítka se stylem WS_TABSTOP|

Při vytváření ovládacího prvku button rastrový obrázek, nastavte styl BS_OWNERDRAW k určení, že je tlačítko vykreslovaných vlastníkem. To způsobí, že Windows k odesílání zpráv WM_MEASUREITEM a WM_DRAWITEM tlačítka; rozhraní framework zpracovává tyto zprávy a spravuje vzhled tlačítka za vás.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Vytvoření ovládacího prvku tlačítko s rastrovým v klientské oblasti okna.

1. Vytváření imagí jednou až čtyřmi rastrový obrázek pro tlačítko.

1. Vytvořit [cbitmapbutton –](#cbitmapbutton) objektu.

1. Volání [vytvořit](../../mfc/reference/cbutton-class.md#create) funkce vytvoření ovládacího prvku tlačítko Windows a připojte ji k `CBitmapButton` objektu.

1. Volání [LoadBitmaps](#loadbitmaps) členskou funkci rastrový obrázek tlačítko zkonstruován načtení prostředků rastrového obrázku.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Vložení ovládacích prvků rastrového obrázku tlačítka v dialogovém okně

1. Vytváření imagí jednou až čtyřmi rastrový obrázek pro tlačítko.

1. Vytvoření šablony dialogového okna tlačítko vykreslené vlastníkem umístěn, ve kterém chcete tlačítko rastrového obrázku. Velikost tlačítka v šabloně není důležitá.

1. Nastavit popisek tlačítka na hodnotu, jako je například "MYIMAGE" a definovat symbol pro tlačítko například IDC_MYIMAGE.

1. Skript prostředků vaší aplikace poskytují všechny obrázky vytvořené na tlačítku pro ID vytvořený přidáním jedním z písmen "U", "D", "F" nebo "X" (pro nahoru, dolů, zaměřuje a zakázán) Chcete-li řetězec použitý pro Titulek tlačítka v kroku 3. Pro "MYIMAGE" popisek tlačítka pro ID může být například "MYIMAGEU", "MYIMAGED", "MYIMAGEF" a "MYIMAGEX." Můžete **musí** zadat ID vašeho rastrové obrázky do dvojitých uvozovek. V opačném případě editor prostředků přiřadí k prostředku celé číslo a knihovny MFC se nezdaří při načítání obrázku.

1. Ve třídě vaší aplikace dialogové okno (odvozený od `CDialog`), přidejte `CBitmapButton` členský objekt.

1. V `CDialog` objektu [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) rutinní, volání `CBitmapButton` objektu [AutoLoad](#autoload) funkce, jako parametry pomocí ID ovládacího prvku tlačítka a `CDialog` objektu **to** ukazatele.

Pokud chcete pro zpracování zpráv s oznámením Windows, jako je například BN_CLICKED, odesílá se tlačítko s rastrovým ovládacím prvkem k nadřazené úloze (obvykle třída odvozená z `CDialog`), přidejte do `CDialog`– odvozeného objektu členem položku a obslužná rutina zprávy map zpráv funkce pro každou zprávu. Oznámení zaslaná z `CBitmapButton` se shodují s nastaveními odesílaných [CButton](../../mfc/reference/cbutton-class.md) objektu.

Třída [ctoolbar –](../../mfc/reference/ctoolbar-class.md) přebírá jiný přístup na rastrového obrázku tlačítka.

Další informace o `CBitmapButton`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

##  <a name="autoload"></a>  CBitmapButton::AutoLoad

Přidruží tlačítko v dialogovém okně objektu `CBitmapButton` třídy, načte bitmap(s) podle názvu a velikosti tlačítko Přizpůsobit rastrový obrázek.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
ID ovládacího prvku tlačítka

*pParent*<br/>
Ukazatel na objekt, který vlastní tlačítka.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Použití `AutoLoad` funkce lze inicializovat na vykreslené vlastníkem tlačítko v dialogovém okně rastrového obrázku tlačítka. Pokyny k použití této funkce jsou v poznámky pro `CBitmapButton` třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

##  <a name="cbitmapbutton"></a>  CBitmapButton::CBitmapButton

Vytvoří `CBitmapButton` objektu.

```
CBitmapButton();
```

### <a name="remarks"></a>Poznámky

Po vytvoření jazyka C++ `CBitmapButton` objektu, volejte [CButton::Create](../../mfc/reference/cbutton-class.md#create) vytvořit ovládací prvek tlačítka Windows a připojte ji k `CBitmapButton` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

##  <a name="loadbitmaps"></a>  CBitmapButton::LoadBitmaps

Tuto funkci použít, pokud chcete načíst bitmapové obrázky identifikovat podle jejich názvy prostředků nebo ID čísla nebo, pokud nelze použít `AutoLoad` fungovat, protože například vytváříte rastrového obrázku tlačítka, který není součástí dialogového okna.

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

*lpszBitmapResource*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název rastrový obrázek pro normální rastrového obrázku tlačítka nebo "do" stavu. Požadováno.

*lpszBitmapResourceSel*<br/>
Odkazuje na řetězec zakončený hodnotou null, která obsahuje název rastrový obrázek pro tlačítko s rastrovým vybraných nebo "dolů" stavu. Může mít hodnotu NULL.

*lpszBitmapResourceFocus*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název rastrový obrázek pro tlačítko rastrový obrázek, zaměřuje stavu. Může mít hodnotu NULL.

*lpszBitmapResourceDisabled*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název rastrový obrázek pro tlačítko rastrový obrázek zakázaném stavu. Může mít hodnotu NULL.

*nIDBitmapResource*<br/>
Určuje identifikační číslo prostředku rastrového obrázku tlačítka normální nebo "do" stavu prostředku rastrového obrázku. Požadováno.

*nIDBitmapResourceSel*<br/>
Určuje identifikační číslo prostředku prostředku rastrového obrázku pro tlačítko s rastrovým vybraných nebo "dolů" stavu. Může být 0.

*nIDBitmapResourceFocus*<br/>
Určuje identifikační číslo prostředku prostředku rastrového obrázku pro cílené stav rastrového obrázku tlačítka. Může být 0.

*nIDBitmapResourceDisabled*<br/>
Určuje identifikační číslo prostředku prostředku rastrového obrázku pro tlačítko rastrový obrázek zakázaném stavu. Může být 0.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

##  <a name="sizetocontent"></a>  CBitmapButton::SizeToContent

Voláním této funkce velikost rastrového obrázku tlačítka na velikost rastrového obrázku.

```
void SizeToContent();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC CTRLTEST](../../visual-cpp-samples.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

