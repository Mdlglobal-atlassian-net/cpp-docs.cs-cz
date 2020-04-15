---
title: Třída CVSListBox
ms.date: 11/19/2018
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
ms.openlocfilehash: 4ea48a263a01133419067979ee5fa3e62105c7f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373192"
---
# <a name="cvslistbox-class"></a>Třída CVSListBox

Třída `CVSListBox` podporuje upravitelný seznam ovládacího prvku.

## <a name="syntax"></a>Syntaxe

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CVSlistBox::CVSListBox](#cvslistbox)|Vytvoří `CVSListBox` objekt.|
|`CVSListBox::~CVSListBox`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CVSlistBox::Přidat položku](#additem)|Přidá řetězec do ovládacího prvku seznamu. (Přepíše `CVSListBoxBase::AddItem`.)|
|[CVSListBox::Upravit položku](#edititem)|Spustí operaci úprav textu položky ovládacího prvku seznamu. (Přepíše `CVSListBoxBase::EditItem`.)|
|[CVSListBox::GetCount](#getcount)|Načte počet řetězců v ovládacím prvku upravitelného seznamu. (Přepíše `CVSListBoxBase::GetCount`.)|
|[CVSlistBox::GetItemData](#getitemdata)|Načte 32bitovou hodnotu specifickou pro aplikaci, která je přidružena k upravitelné položce ovládacího prvku seznamu. (Přepíše `CVSListBoxBase::GetItemData`.)|
|[CVSlistBox::GetItemText](#getitemtext)|Načte text upravitelné položky ovládacího prvku seznamu. (Přepíše `CVSListBoxBase::GetItemText`.)|
|[CVSListBox::GetSelItem](#getselitem)|Načte index aktuálně vybrané položky založený na nule v ovládacím prvku upravitelného seznamu. (Přepíše `CVSListBoxBase::GetSelItem`.)|
|`CVSListBox::PreTranslateMessage`|Přeloží zprávy okna před jejich odesláním do funkcí [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systému Windows. Další informace a syntaxe metody naleznete [v tématu CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Přepíše `CVSListBoxBase::PreTranslateMessage`.)|
|[CVSListBox::Odebrat položku](#removeitem)|Odebere položku z ovládacího prvku upravitelného seznamu. (Přepíše `CVSListBoxBase::RemoveItem`.)|
|[CVSListBox::Vybrat položku](#selectitem)|Vybere upravitelný řetězec ovládacího prvku seznamu. (Přepíše `CVSListBoxBase::SelectItem`.)|
|[CVSListBox::SetItemData](#setitemdata)|Přidruží 32bitovou hodnotu specifickou pro aplikaci k upravitelné položce ovládacího prvku seznamu. (Přepíše `CVSListBoxBase::SetItemData`.)|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CVSListBox::GetListHwnd](#getlisthwnd)|Vrátí popisovač aktuálního ovládacího prvku zobrazení vloženého seznamu.|

## <a name="remarks"></a>Poznámky

Třída `CVSListBox` poskytuje sadu tlačítek pro úpravy, které umožňují uživateli vytvářet, upravovat, odstraňovat nebo měnit uspořádání položek v ovládacím prvku seznamu.

Následuje obrázek upravitelného ovládacího prvku seznamu. Pro úpravy je vybrána druhá položka seznamu s názvem "Položka 2".

![Ovládací prvek CVSListBox](../../mfc/reference/media/cvslistbox.png "Ovládací prvek CVSListBox")

Pokud pomocí editoru prostředků přidáte upravitelný ovládací prvek seznamu, všimněte si, že podokno **panelu nástrojů** editoru neposkytuje předdefinovaný ovládací prvek upravitelného seznamu. Místo toho přidejte statický ovládací prvek, jako je například ovládací prvek **Pole skupiny.** Rozhraní framework používá statický ovládací prvek jako zástupný symbol k určení velikosti a umístění upravitelného ovládacího prvku seznamu.

Chcete-li použít upravitelný ovládací prvek seznamu `CVSListBox` v šabloně dialogového okna, deklarujte proměnnou ve třídě dialogového okna. Chcete-li podporovat výměnu dat mezi proměnnou a `DoDataExchange` ovládacím prvkem, definujte položku `DDX_Control` makra v metodě dialogového okna. Ve výchozím nastavení je upravitelný ovládací prvek seznamu vytvořen bez tlačítek pro úpravy. Pomocí zděděné metody CVSListBoxBase::SetStandardButtons povolte tlačítka pro úpravy.

Další informace naleznete v adresáři `New Controls` Ukázky, v vzorce, v souborech Page3.cpp a Page3.h.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxvslistbox.h

## <a name="cvslistboxadditem"></a><a name="additem"></a>CVSlistBox::Přidat položku

Přidá řetězec do ovládacího prvku seznamu.

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*strIext*<br/>
[v] Odkaz na řetězec.

*dwData*<br/>
[v] 32bitová hodnota specifická pro aplikaci, která je přidružena k řetězci. Výchozí hodnota je 0.

*iIndex*<br/>
[v] Nula na základě indexu pozice, která bude držet řetězec. Pokud je parametr *iIndex* -1, řetězec je přidán na konec seznamu. Výchozí hodnota je -1.

### <a name="return-value"></a>Návratová hodnota

Index na základě nuly pozice řetězce v ovládacím prvku seznamu.

### <a name="remarks"></a>Poznámky

Pomocí metody [CVSListBox::GetItemData](#getitemdata) načtěte hodnotu, která je určena parametrem *dwData.* Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na jiná data.

## <a name="cvslistboxcvslistbox"></a><a name="cvslistbox"></a>CVSlistBox::CVSListBox

Vytvoří `CVSListBox` objekt.

```
CVSListBox();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cvslistboxedititem"></a><a name="edititem"></a>CVSListBox::Upravit položku

Spustí operaci úprav textu položky ovládacího prvku seznamu.

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Nulový index položky ovládacího prvku seznamu.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud se operace úprav spustí úspěšně; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Uživatel spustí operaci úprav poklepáním na popisek položky nebo stisknutím klávesy **F2** nebo **MEZERNÍK,** pokud má položka fokus.

## <a name="cvslistboxgetcount"></a><a name="getcount"></a>CVSListBox::GetCount

Načte počet řetězců v ovládacím prvku upravitelného seznamu.

```
virtual int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v ovládacím prvku seznamu.

### <a name="remarks"></a>Poznámky

Všimněte si, že počet je o jeden větší než hodnota indexu poslední položky, protože index je založen na nule.

## <a name="cvslistboxgetitemdata"></a><a name="getitemdata"></a>CVSlistBox::GetItemData

Načte 32bitovou hodnotu specifickou pro aplikaci, která je přidružena k upravitelné položce ovládacího prvku seznamu.

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Index ovládacího prvku na základě nuly upravitelné položky seznamu.

### <a name="return-value"></a>Návratová hodnota

32bitová hodnota, která je přidružena k zadané položce.

### <a name="remarks"></a>Poznámky

Pomocí metody [CVSListBox::SetItemData](#setitemdata) nebo [CVSListBox::AddItem](#additem) přidružte 32bitovou hodnotu k položce ovládacího prvku seznamu. Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na jiná data.

## <a name="cvslistboxgetitemtext"></a><a name="getitemtext"></a>CVSlistBox::GetItemText

Načte text upravitelné položky ovládacího prvku seznamu.

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Index ovládacího prvku na základě nuly upravitelné položky seznamu.

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje text zadané položky.

### <a name="remarks"></a>Poznámky

## <a name="cvslistboxgetlisthwnd"></a><a name="getlisthwnd"></a>CVSListBox::GetListHwnd

Vrátí popisovač aktuálního ovládacího prvku zobrazení vloženého seznamu.

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač prvku zobrazení vloženého seznamu.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete načíst popisovač do ovládacího prvku zobrazení vloženého seznamu, který podporuje třídu. `CVSListBox`

## <a name="cvslistboxgetselitem"></a><a name="getselitem"></a>CVSListBox::GetSelItem

Načte index aktuálně vybrané položky založený na nule v ovládacím prvku upravitelného seznamu.

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je tato metoda úspěšná, index aktuálně vybrané položky založený na nule; jinak -1.

### <a name="remarks"></a>Poznámky

## <a name="cvslistboxremoveitem"></a><a name="removeitem"></a>CVSListBox::Odebrat položku

Odebere položku z ovládacího prvku upravitelného seznamu.

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Index ovládacího prvku na základě nuly upravitelné položky seznamu.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je zadaná položka odebrána; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cvslistboxselectitem"></a><a name="selectitem"></a>CVSListBox::Vybrat položku

Vybere upravitelný řetězec ovládacího prvku seznamu.

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>Parametry

*iPoložka*<br/>
[v] Index ovládacího prvku na základě nuly upravitelné položky seznamu.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda vybere zadanou položku a pokud je požadována, posune položku do zobrazení.

## <a name="cvslistboxsetitemdata"></a><a name="setitemdata"></a>CVSListBox::SetItemData

Přidruží 32bitovou hodnotu specifickou pro aplikaci k upravitelné položce ovládacího prvku seznamu.

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Index ovládacího prvku na základě nuly upravitelné položky seznamu.

*dwData*<br/>
[v] 32bitová hodnota. Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na jiná data.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
