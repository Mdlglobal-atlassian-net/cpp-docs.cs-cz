---
title: CVSListBox – třída
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
ms.openlocfilehash: 6a33f5b64c5094bfe2ca2ff259b5cd8654058ed3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502233"
---
# <a name="cvslistbox-class"></a>CVSListBox – třída

`CVSListBox` Třída podporuje upravitelný ovládací prvek seznamu.

## <a name="syntax"></a>Syntaxe

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CVSListBox::CVSListBox](#cvslistbox)|`CVSListBox` Vytvoří objekt.|
|`CVSListBox::~CVSListBox`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CVSListBox::AddItem](#additem)|Přidá řetězec do ovládacího prvku seznamu. (Overrides `CVSListBoxBase::AddItem`.)|
|[CVSListBox::EditItem](#edititem)|Spustí operaci Edit na textu položky ovládacího prvku seznamu. (Overrides `CVSListBoxBase::EditItem`.)|
|[CVSListBox:: GetCount](#getcount)|Načte počet řetězců v ovládacím prvku upravitelný seznam. (Overrides `CVSListBoxBase::GetCount`.)|
|[CVSListBox::GetItemData](#getitemdata)|Načte hodnotu 32 specifickou pro aplikaci, která je přidružena k položce ovládacího prvku seznamu, kterou lze upravovat. (Overrides `CVSListBoxBase::GetItemData`.)|
|[CVSListBox::GetItemText](#getitemtext)|Načte text položky ovládacího prvku upravitelný seznam. (Overrides `CVSListBoxBase::GetItemText`.)|
|[CVSListBox::GetSelItem](#getselitem)|Načte index aktuálně vybrané položky v rámci upravitelného ovládacího prvku seznamu s nulovým základem. (Overrides `CVSListBoxBase::GetSelItem`.)|
|`CVSListBox::PreTranslateMessage`|Přeloží zprávy oken před odesláním do funkcí Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Další informace a syntaxi metod naleznete v tématu [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Overrides `CVSListBoxBase::PreTranslateMessage`.)|
|[CVSListBox:: RemoveItem](#removeitem)|Odebere položku z upravitelného ovládacího prvku seznamu. (Overrides `CVSListBoxBase::RemoveItem`.)|
|[CVSListBox::SelectItem](#selectitem)|Vybere upravitelný řetězec ovládacího prvku seznamu. (Overrides `CVSListBoxBase::SelectItem`.)|
|[CVSListBox::SetItemData](#setitemdata)|Přidruží hodnotu 32-bit specifickou pro aplikaci s upravitelnou položkou ovládacího prvku seznamu. (Overrides `CVSListBoxBase::SetItemData`.)|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CVSListBox::GetListHwnd](#getlisthwnd)|Vrátí popisovač k aktuálnímu ovládacímu prvku zobrazení seznamu.|

## <a name="remarks"></a>Poznámky

`CVSListBox` Třída poskytuje sadu tlačítek pro úpravy, které uživateli umožňují vytvořit, upravit, odstranit nebo změnit uspořádání položek v ovládacím prvku seznam.

Následuje obrázek ovládacího prvku upravitelný seznam. Druhá položka seznamu, která má názvem "Item2", je vybrána pro úpravy.

![Ovládací prvek CVSListBox](../../mfc/reference/media/cvslistbox.png "Ovládací prvek CVSListBox")

Použijete-li Editor prostředků k přidání ovládacího prvku upravitelný seznam, Všimněte si, že podokno **sady nástrojů** editoru neposkytuje předem definovaný ovládací prvek seznamu, který lze upravit. Místo toho přidejte statický ovládací prvek, jako je například ovládací prvek **skupinový rámeček** . Rozhraní používá statický ovládací prvek jako zástupný symbol k určení velikosti a umístění ovládacího prvku upravitelný seznam.

Chcete-li použít upravitelný ovládací prvek seznamu v šabloně dialogového okna, `CVSListBox` deklarujte proměnnou ve třídě dialogového okna. Pro podporu výměny dat mezi proměnnou a ovládacím prvkem definujte `DDX_Control` položku makra `DoDataExchange` v metodě dialogového okna. Ve výchozím nastavení je ovládací prvek upravitelný seznam vytvořen bez tlačítek pro úpravy. Pomocí zděděné metody CVSListBoxBase:: SetStandardButtons povolte tlačítka pro úpravy.

Další informace naleznete v adresáři Samples, `New Controls` Sample, PAGE3. cpp a PAGE3. h Files.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxvslistbox. h

##  <a name="additem"></a>CVSListBox:: AddItem

Přidá řetězec do ovládacího prvku seznamu.

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*strIext*<br/>
pro Odkaz na řetězec.

*dwData*<br/>
pro Hodnota 32 specifická pro aplikaci, která je přidružena k řetězci. Výchozí hodnota je 0.

*iIndex*<br/>
pro Index na základě nuly pozice, která bude obsahovat řetězec. Pokud je parametr *iIndex* -1, řetězec se přidá na konec seznamu. Výchozí hodnota je-1.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule pozice řetězce v ovládacím prvku seznamu.

### <a name="remarks"></a>Poznámky

Použijte metodu [CVSListBox:: GetItemData](#getitemdata) k načtení hodnoty, která je určena parametrem *dwData* . Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na jiná data.

##  <a name="cvslistbox"></a>CVSListBox::CVSListBox

`CVSListBox` Vytvoří objekt.

```
CVSListBox();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="edititem"></a>CVSListBox:: EditItem

Spustí operaci Edit na textu položky ovládacího prvku seznamu.

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
pro Index založený na nule položky ovládacího prvku seznamu

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se operace úpravy spustí úspěšně; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Uživatel spustí operaci úprav Poklikáním na popisek položky nebo stisknutím klávesy **F2** nebo **MEZERNÍK** , pokud má položka fokus.

##  <a name="getcount"></a>CVSListBox:: GetCount

Načte počet řetězců v ovládacím prvku upravitelný seznam.

```
virtual int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v ovládacím prvku seznam.

### <a name="remarks"></a>Poznámky

Všimněte si, že počet je větší než hodnota indexu poslední položky, protože index je založený na nule.

##  <a name="getitemdata"></a>CVSListBox::GetItemData

Načte hodnotu 32 specifickou pro aplikaci, která je přidružena k položce ovládacího prvku seznamu, kterou lze upravovat.

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
pro Index založený na nule pro upravitelnou položku ovládacího prvku seznamu.

### <a name="return-value"></a>Návratová hodnota

Hodnota 32, která je přidružena k zadané položce.

### <a name="remarks"></a>Poznámky

Použijte metodu [CVSListBox:: SetItemData](#setitemdata) nebo [CVSListBox:: AddItem](#additem) k přidružení hodnoty 32-bit k položce ovládacího prvku seznamu. Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na jiná data.

##  <a name="getitemtext"></a>CVSListBox::GetItemText

Načte text položky ovládacího prvku upravitelný seznam.

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
pro Index založený na nule pro upravitelnou položku ovládacího prvku seznamu.

### <a name="return-value"></a>Návratová hodnota

Objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který obsahuje text zadané položky.

### <a name="remarks"></a>Poznámky

##  <a name="getlisthwnd"></a>CVSListBox::GetListHwnd

Vrátí popisovač k aktuálnímu ovládacímu prvku zobrazení seznamu.

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro ovládací prvek vloženého zobrazení seznamu.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li načíst popisovač do ovládacího prvku zobrazení seznamu, který `CVSListBox` podporuje třídu.

##  <a name="getselitem"></a>CVSListBox::GetSelItem

Načte index aktuálně vybrané položky v rámci upravitelného ovládacího prvku seznamu s nulovým základem.

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je tato metoda úspěšná, index založený na nule aktuálně vybrané položky; v opačném případě-1.

### <a name="remarks"></a>Poznámky

##  <a name="removeitem"></a>CVSListBox:: RemoveItem

Odebere položku z upravitelného ovládacího prvku seznamu.

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
pro Index založený na nule pro upravitelnou položku ovládacího prvku seznamu.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadaná položka odebrána; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="selectitem"></a>CVSListBox::SelectItem

Vybere upravitelný řetězec ovládacího prvku seznamu.

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>Parametry

*iItem*<br/>
pro Index založený na nule pro upravitelnou položku ovládacího prvku seznamu.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vybere určenou položku a pokud je vyžadována, posuňte položku do zobrazení.

##  <a name="setitemdata"></a>CVSListBox::SetItemData

Přidruží hodnotu 32-bit specifickou pro aplikaci s upravitelnou položkou ovládacího prvku seznamu.

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
pro Index založený na nule pro upravitelnou položku ovládacího prvku seznamu.

*dwData*<br/>
pro Hodnota 32. Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na jiná data.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
