---
title: Třída CAnimateCtrl
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
ms.openlocfilehash: fcee569659d732c26e274c8ca189042a16f13557
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371072"
---
# <a name="canimatectrl-class"></a>Třída CAnimateCtrl

Poskytuje funkce ovládacího prvku společné animace systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|Vytvoří `CAnimateCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimateCtrl::Zavřít](#close)|Zavře klip AVI.|
|[CAnimateCtrl::Vytvořit](#create)|Vytvoří ovládací prvek animace a `CAnimateCtrl` připojí jej k objektu.|
|[CAnimateCtrl::CreateEx](#createex)|Vytvoří ovládací prvek animace se zadanými rozšířenými `CAnimateCtrl` styly systému Windows a připojí jej k objektu.|
|[CAnimateCtrl::Přehrávání](#isplaying)|Označuje, zda se přehrává klip AVI (Audio-Video Interleaved).|
|[CAnimateCtrl::Otevřít](#open)|Otevře klip AVI ze souboru nebo prostředku a zobrazí první snímek.|
|[CAnimateCtrl::Play](#play)|Přehraje klip AVI bez zvuku.|
|[CAnimateCtrl::Hledat](#seek)|Zobrazí vybraný snímek klipu AVI.|
|[CAnimateCtrl::Stop](#stop)|Přestane přehrávat klip AVI.|

## <a name="remarks"></a>Poznámky

Tento ovládací prvek `CAnimateCtrl` (a tedy třída) je k dispozici pouze pro programy spuštěné v systémech Windows 95, Windows 98 a Windows NT verze 3.51 a novějších.

Ovládací prvek animace je obdélníkové okno, které zobrazuje klip ve formátu AVI (Audio Video Interleaved), což je standardní formát windows video/audio. Klip AVI je řada bitmapových snímků, jako je film.

Ovládací prvky animace mohou přehrávat pouze jednoduché klipy AVI. Klipy, které mají být přehrávány ovládacím prvkem animace, musí splňovat následující požadavky:

- Musí existovat přesně jeden datový proud videa a musí mít alespoň jeden snímek.

- V souboru mohou být maximálně dva datové proudy (obvykle druhý datový proud, pokud je přítomen, je zvukový datový proud, i když ovládací prvek animace ignoruje informace o zvuku).

- Klip musí být buď nekomprimovaný, nebo komprimovaný s kompresí RLE8.

- V datovém proudu videa nejsou povoleny žádné změny palety.

Můžete přidat klip AVI do aplikace jako prostředek AVI, nebo může doprovázet vaši aplikaci jako samostatný soubor AVI.

Vzhledem k tomu, že vlákno pokračuje při provádění, zatímco je zobrazen klip AVI, jedním z běžných použití pro ovládací prvek animace je označení aktivity systému během zdlouhavé operace. Například dialogové okno Najít průzkumníka souborů zobrazí při hledání souboru pohyblivou lupu.

Pokud vytvoříte `CAnimateCtrl` objekt v dialogovém okně nebo z prostředku dialogu pomocí dialogového editoru, bude automaticky zničen, když uživatel zavře dialogové okno.

Pokud vytvoříte `CAnimateCtrl` objekt v okně, bude pravděpodobně nutné jej zničit. Pokud vytvoříte `CAnimateCtrl` objekt v zásobníku, je automaticky zničen. Pokud vytvoříte `CAnimateCtrl` objekt na haldě pomocí **nové** funkce, musíte volat **delete** na objekt zničit. Pokud odvodit `CAnimateCtrl` novou třídu z a přidělit `CAnimateCtrl` všechny paměti v této třídě, přepsat destruktor nadispose přidělení.

Další informace o `CAnimateCtrl`použití naleznete v [tématu Controls](../../mfc/controls-mfc.md) and [Using CAnimateCtrl](../../mfc/using-canimatectrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a>CAnimateCtrl::CAnimateCtrl

Vytvoří `CAnimateCtrl` objekt.

```
CAnimateCtrl();
```

### <a name="remarks"></a>Poznámky

Před provedením jakékoli další operace s objektem, který vytvoříte, je nutné zavolat členská funkci [Create.](#create)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a>CAnimateCtrl::Zavřít

Zavře klip AVI, který byl dříve otevřen v ovládacím prvku animace (pokud existuje) a odebere jej z paměti.

```
BOOL Close();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="example"></a>Příklad

  Viz příklad [canimatectrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreate"></a><a name="create"></a>CAnimateCtrl::Vytvořit

Vytvoří ovládací prvek animace a `CAnimateCtrl` připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl ovládacího prvku animace. Použijte libovolnou kombinaci stylů oken popsaných v části Poznámky níže a styly ovládacích prvků animace popsané ve [stylech řízení animací](/windows/win32/Controls/animation-control-styles) v sadě Windows SDK.

*Rect*<br/>
Určuje umístění a velikost ovládacího prvku animace. Může to být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/windows/win32/api/windef/ns-windef-rect) struktury.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího `CDialog`prvku animace, obvykle . Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku animace.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CAnimateCtrl` ve dvou krocích. Nejprve zavolejte konstruktoru `Create`a potom volání , který vytvoří `CAnimateCtrl` ovládací prvek animace a připojí jej k objektu.

Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) na ovládací prvek animace.

- WS_CHILD vždy

- WS_VISIBLE Obvykle

- WS_DISABLED Zřídka

Pokud chcete použít rozšířené styly oken s ovládacím `Create`prvkem animace, zavolejte [createex](#createex) místo .

Kromě výše uvedených stylů oken můžete použít jeden nebo více stylů ovládacího prvku animace na ovládací prvek animace. Další informace o [stylech ovládacích prvků animací](/windows/win32/Controls/animation-control-styles)naleznete v ksi sady Windows SDK .

### <a name="example"></a>Příklad

  Viz příklad [canimatectrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreateex"></a><a name="createex"></a>CAnimateCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) a `CAnimateCtrl` přidruží jej k objektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyl*<br/>
Určuje rozšířený styl vytvářeného ovládacího prvku. Seznam rozšířených stylů systému Windows naleznete v parametru *dwExStyle* pro [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) v sadě Windows SDK.

*dwStyl*<br/>
Určuje styl ovládacího prvku animace. Použijte libovolnou kombinaci stylů oken a ovládacích prvků animace popsanou ve [stylech ovládacího prvku animace](/windows/win32/Controls/animation-control-styles) v sadě Windows SDK.

*Rect*<br/>
Odkaz na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu popisující velikost a umístění okna, které mají být vytvořeny, v klientských souřadnicích *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládací prvek.

*Nid*<br/>
ID podřízeného okna ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Místo `CreateEx` funkce [Vytvořit](#create) použijte použití rozšířených stylů systému Windows určených **předmluvou**rozšířeného stylu systému Windows WS_EX_ .

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a>CAnimateCtrl::Přehrávání

Označuje, zda se přehrává klip AVI (Audio-Video Interleaved).

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se přehrává klip AVI; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu ACM_ISPLAYING,](/windows/win32/Controls/acm-isplaying) která je popsána v sadě Windows SDK.

## <a name="canimatectrlopen"></a><a name="open"></a>CAnimateCtrl::Otevřít

Voláním této funkce otevřete klip AVI a zobrazte jeho první snímek.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>Parametry

*název souboru lpsz*<br/>
Objekt `CString` nebo ukazatel na řetězec s nulovým ukončením, který obsahuje název souboru AVI nebo název prostředku AVI. Pokud je tento parametr NULL, systém zavře klip AVI, který byl dříve otevřen pro ovládací prvek animace, pokud existuje.

*Nid*<br/>
Identifikátor prostředku AVI. Pokud je tento parametr NULL, systém zavře klip AVI, který byl dříve otevřen pro ovládací prvek animace, pokud existuje.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Prostředek AVI je načten z modulu, který vytvořil ovládací prvek animace.

`Open`nepodporuje zvuk v klipu AVI; můžete otevřít pouze tiché klipy AVI.

Pokud má ovládací `ACS_AUTOPLAY` prvek animace styl, ovládací prvek animace automaticky začne přehrávat klip ihned po jeho otevření. Bude pokračovat v přehrávání klipu na pozadí, zatímco vlákno pokračuje v provádění. Po dokončení přehrávání se klip automaticky opakuje.

Pokud má ovládací `ACS_CENTER` prvek animace styl, klip AVI bude vystředěn v ovládacím prvku a velikost ovládacího prvku se nezmění. Pokud ovládací prvek animace `ACS_CENTER` nemá styl, bude změnit velikost ovládacího prvku při otevření klipu AVI na velikost obrazů v klipu AVI. Pozice levého horního rohu ovládacího prvku se nezmění, pouze velikost ovládacího prvku.

Pokud má ovládací `ACS_TRANSPARENT` prvek animace styl, první snímek bude nakreslen pomocí průhledného pozadí, nikoli barvy pozadí určené v animačním klipu.

### <a name="example"></a>Příklad

  Viz příklad [canimatectrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlplay"></a><a name="play"></a>CAnimateCtrl::Play

Volání této funkce pro přehrání klipu AVI v ovládacím prvku animace.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>Parametry

*nFrom*<br/>
Nulový index snímku, kde začíná přehrávání. Hodnota musí být menší než 65 536. Hodnota 0 znamená, že začíná prvním snímkem v klipu AVI.

*nChcete-li*<br/>
Nulový index snímku, kde přehrávání končí. Hodnota musí být menší než 65 536. Hodnota - 1 znamená konec s posledním snímkem v klipu AVI.

*nRep*<br/>
Počet opakování klipu AVI. Hodnota - 1 znamená přehrát soubor neomezeně dlouho.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Ovládací prvek animace přehraje klip na pozadí, zatímco vlákno pokračuje v provádění. Pokud má `ACS_TRANSPARENT` ovládací prvek animace styl, klip AVI se přehraje pomocí průhledného pozadí, nikoli barvy pozadí určené v animačním klipu.

### <a name="example"></a>Příklad

  Viz příklad [canimatectrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlseek"></a><a name="seek"></a>CAnimateCtrl::Hledat

Volání této funkce staticky zobrazit jeden snímek vašeho Klip AVI.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>Parametry

*nChcete-li*<br/>
Nulový index rámce, který se má zobrazit. Hodnota musí být menší než 65 536. Hodnota 0 znamená zobrazení prvního snímku v klipu AVI. Hodnota -1 znamená zobrazení posledního snímku v klipu AVI.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Pokud má `ACS_TRANSPARENT` ovládací prvek animace styl, bude klip AVI nakreslen pomocí průhledného pozadí, nikoli barvy pozadí určené v animačním klipu.

### <a name="example"></a>Příklad

Viz příklad [canimatectrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlstop"></a><a name="stop"></a>CAnimateCtrl::Stop

Voláním této funkce můžete zastavit přehrávání klipu AVI v ovládacím prvku animace.

```
BOOL Stop();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="example"></a>Příklad

  Viz příklad [canimatectrl::CAnimateCtrl](#canimatectrl).

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Vytvořit](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
