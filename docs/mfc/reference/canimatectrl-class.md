---
title: Atributu CAnimateCtrl – třída
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
ms.openlocfilehash: 18adead999f26768ae669d3a829b557bf9632a29
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177444"
---
# <a name="canimatectrl-class"></a>Atributu CAnimateCtrl – třída

Poskytuje funkce pro běžný ovládací prvek animací Windows.

## <a name="syntax"></a>Syntaxe

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|`CAnimateCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAnimateCtrl::Close](#close)|Zavře klip AVI.|
|[CAnimateCtrl::Create](#create)|Vytvoří ovládací prvek animace a připojí ho k `CAnimateCtrl` objektu.|
|[CAnimateCtrl::CreateEx](#createex)|Vytvoří ovládací prvek animace se zadanými rozšířenými styly Windows a připojí ho k `CAnimateCtrl` objektu.|
|[CAnimateCtrl::IsPlaying](#isplaying)|Označuje, zda je přehráván klip přehrávaný zvukovým videem (AVI).|
|[CAnimateCtrl::Open](#open)|Otevře klip AVI ze souboru nebo prostředku a zobrazí první snímek.|
|[CAnimateCtrl::Play](#play)|Vyhrává klip AVI bez zvuku.|
|[Atributu CAnimateCtrl:: Seek](#seek)|Zobrazí vybraný jeden rámec klipu AVI.|
|[Atributu CAnimateCtrl:: stop](#stop)|Zastaví přehrávání klipu AVI.|

## <a name="remarks"></a>Poznámky

Tento ovládací prvek (a `CAnimateCtrl` třída) je k dispozici pouze pro programy, které jsou spuštěny v systému Windows 95, Windows 98 a Windows NT verze 3,51 a novější.

Ovládací prvek animace je obdélníkové okno, ve kterém se zobrazuje klip ve formátu AVI (audio video s pokládaným), což je standardní formát Windows Video/zvuk. Klip AVI je série rastrových snímků, jako je třeba film.

Ovládací prvky animace mohou přehrávat pouze jednoduché klipy AVI. Kliparty, které mají být přehrávány ovládacím prvkem animace, musí splňovat následující požadavky:

- Musí existovat právě jeden datový proud videa a musí obsahovat alespoň jeden snímek.

- V souboru může být nejvýše dva proudy (obvykle druhý datový proud, pokud je přítomen, je zvukový stream, i když ovládací prvek animace ignoruje zvukové informace).

- Klip musí být buď uncompressed, nebo komprimován pomocí RLE8 Compression.

- V datovém proudu videa nejsou povoleny žádné změny palety.

Klip AVI můžete přidat do aplikace jako prostředek AVI, nebo může být součástí aplikace jako samostatný soubor AVI.

Vzhledem k tomu, že vaše vlákno pokračuje v době, kdy se zobrazuje klip AVI, jedno běžné použití pro ovládací prvek animace je označovat aktivitu systému během zdlouhavé operace. Například dialogové okno najít v Průzkumníkovi souborů zobrazí přesunutí lupy při hledání souboru v systému.

Pokud vytvoříte `CAnimateCtrl` objekt v rámci dialogového okna nebo z prostředku dialogového okna pomocí editoru dialogového okna, bude automaticky zničen, když uživatel zavře dialogové okno.

Pokud vytvoříte `CAnimateCtrl` objekt v rámci okna, může být nutné jej zničit. Vytvoříte-li `CAnimateCtrl` objekt v zásobníku, bude automaticky zničen. Vytvoříte `CAnimateCtrl` -li objekt na haldě pomocí **nové** funkce, je nutné volat metodu **Delete** objektu pro zničení. Pokud odvodit novou třídu z `CAnimateCtrl` a přidělíte jakoukoli paměť v této třídě, `CAnimateCtrl` přepište destruktor k Dispose přidělení.

Další informace o použití `CAnimateCtrl`naleznete v tématu [Controls](../../mfc/controls-mfc.md) and [using atributu CAnimateCtrl](../../mfc/using-canimatectrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="canimatectrl"></a>Atributu CAnimateCtrl:: atributu CAnimateCtrl

`CAnimateCtrl` Vytvoří objekt.

```
CAnimateCtrl();
```

### <a name="remarks"></a>Poznámky

Před provedením jakýchkoli dalších operací s objektem, který vytvoříte, je nutné zavolat funkci [Create](#create) member.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

##  <a name="close"></a>Atributu CAnimateCtrl:: Close

Zavře klip AVI, který byl dříve otevřen v ovládacím prvku animace (pokud existuje), a odebere jej z paměti.

```
BOOL Close();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CAnimateCtrl:: atributu CAnimateCtrl](#canimatectrl).

##  <a name="create"></a>Atributu CAnimateCtrl:: Create

Vytvoří ovládací prvek animace a připojí ho k `CAnimateCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl ovládacího prvku animace. Použijte libovolnou kombinaci stylů Windows popsaných v níže uvedené části poznámky a styly ovládacího prvku animace popsané v tématu [styly ovládacích prvků animace](/windows/win32/Controls/animation-control-styles) v Windows SDK.

*OBD*<br/>
Určuje pozici a velikost ovládacího prvku animace. Může to být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo struktura [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku animace, obvykle a `CDialog`. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku animace.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Vytvoří `CAnimateCtrl` se ve dvou krocích. Nejprve volejte konstruktor a potom zavolejte `Create`, čímž se vytvoří ovládací prvek animace a připojí se `CAnimateCtrl` k objektu.

Použijte následující [Styly okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) pro ovládací prvek animace.

- WS_CHILD vždycky

- WS_VISIBLE obvykle

- WS_DISABLED málokdy

Chcete-li použít rozšířené styly systému Windows s ovládacím prvkem animace, zavolejte [CreateEx](#createex) místo `Create`.

Kromě stylů oken uvedených výše možná budete chtít použít jeden nebo více stylů ovládacího prvku animace pro ovládací prvek animace. Další informace o [stylech ovládacích prvků animace](/windows/win32/Controls/animation-control-styles)naleznete v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CAnimateCtrl:: atributu CAnimateCtrl](#canimatectrl).

##  <a name="createex"></a>Atributu CAnimateCtrl:: CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ho k `CAnimateCtrl` objektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Určuje rozšířený styl ovládacího prvku, který se vytváří. Seznam rozšířených stylů Windows naleznete v parametru *dwExStyle* pro [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v Windows SDK.

*dwStyle*<br/>
Určuje styl ovládacího prvku animace. Použijte libovolnou kombinaci stylů ovládacího prvku okna a animace popsané v Windows SDK [styly ovládacích prvků animace](/windows/win32/Controls/animation-control-styles) .

*OBD*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) popisující velikost a umístění okna, které má být vytvořeno, v souřadnicích klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládacímu prvku.

*nID*<br/>
ID podřízeného okna ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Použijte `CreateEx` místo příkaz [vytvořit](#create) pro použití rozšířených stylů Windows, které jsou určené **WS_EX_** rozšířeným stylem Windows.

##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying

Označuje, zda je přehráván klip přehrávaný zvukovým videem (AVI).

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se klip AVI hraje; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying) , která je popsána v Windows SDK.

##  <a name="open"></a>Atributu CAnimateCtrl:: Open

Voláním této funkce otevřete klip AVI a zobrazíte jeho první snímek.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
`CString` Objekt nebo ukazatel na řetězec zakončený hodnotou null, který obsahuje buď název souboru AVI, nebo název prostředku AVI. Pokud má tento parametr hodnotu NULL, systém zavře klip AVI, který byl dříve otevřen pro ovládací prvek animace, pokud nějaký existuje.

*nID*<br/>
Identifikátor prostředku AVI. Pokud má tento parametr hodnotu NULL, systém zavře klip AVI, který byl dříve otevřen pro ovládací prvek animace, pokud nějaký existuje.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Prostředek AVI je načten z modulu, který vytvořil ovládací prvek animace.

`Open`v klipu AVI nepodporuje zvuk; můžete otevřít jenom tiché klipy AVI.

Má-li ovládací prvek animace `ACS_AUTOPLAY` styl, ovládací prvek animace automaticky začne přehrávat klip ihned po jeho otevření. Bude pokračovat v přehrávání klipu na pozadí, zatímco vaše vlákno pokračuje v provádění. Až se klip dokončí, automaticky se zopakuje.

Má-li ovládací prvek animace `ACS_CENTER` styl, klip AVI bude zarovnán do středu ovládacího prvku a velikost ovládacího prvku se nezmění. Pokud ovládací prvek `ACS_CENTER` animace nemá styl, změní se velikost ovládacího prvku, když je klip AVI otevřen na velikost obrázků v klipu AVI. Pozice levého horního rohu ovládacího prvku se nezmění, pouze velikost ovládacího prvku.

Má-li ovládací prvek animace `ACS_TRANSPARENT` styl, bude první snímek vykreslen pomocí průhledného pozadí namísto barvy pozadí zadané v animovaném klipu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CAnimateCtrl:: atributu CAnimateCtrl](#canimatectrl).

##  <a name="play"></a>Atributu CAnimateCtrl::P – rozložení

Voláním této funkce přehrajete klip AVI v ovládacím prvku animace.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>Parametry

*Nze*<br/>
Index založený na nule snímku, kde začíná přehrávání. Hodnota musí být menší než 65 536. Hodnota 0 znamená, že začne s prvním rámcem v klipu AVI.

*nPokud*<br/>
Index založený na nule snímku, kde se nachází přehrávání konců. Hodnota musí být menší než 65 536. Hodnota-1 znamená konec s posledním snímkem v klipu AVI.

*nRep*<br/>
Počet pokusů klipu AVI pro přehrání. Hodnota-1 znamená, že soubor bude po neomezenou dobu přehrán.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Ovládací prvek animace přehraje klip na pozadí, zatímco vaše vlákno pokračuje v provádění. Pokud má `ACS_TRANSPARENT` ovládací prvek animace styl, klip AVI se přehraje pomocí průhledného pozadí namísto barvy pozadí zadané v animovaném klipu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CAnimateCtrl:: atributu CAnimateCtrl](#canimatectrl).

##  <a name="seek"></a>Atributu CAnimateCtrl:: Seek

Voláním této funkce staticky zobrazíte jeden snímek klipu AVI.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>Parametry

*nPokud*<br/>
Index s nulovým základem rámce, který se má zobrazit Hodnota musí být menší než 65 536. Hodnota 0 znamená, že se v klipu AVI zobrazí první snímek. Hodnota-1 znamená, že se v klipu AVI zobrazí poslední snímek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Pokud má `ACS_TRANSPARENT` ovládací prvek animace styl, klip AVI bude vykreslen pomocí průhledného pozadí namísto barvy pozadí zadané v animovaném klipu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [atributu CAnimateCtrl:: atributu CAnimateCtrl](#canimatectrl).

##  <a name="stop"></a>Atributu CAnimateCtrl:: stop

Voláním této funkce zabráníte přehrávání klipu AVI v ovládacím prvku animace.

```
BOOL Stop();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CAnimateCtrl:: atributu CAnimateCtrl](#canimatectrl).

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
