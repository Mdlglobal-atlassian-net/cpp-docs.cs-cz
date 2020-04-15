---
title: Třída CWinFormsControl
ms.date: 11/04/2016
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
ms.openlocfilehash: c91f50be1ea30efac81ff67c43633bedd7b0ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377179"
---
# <a name="cwinformscontrol-class"></a>Třída CWinFormsControl

Poskytuje základní funkce pro hostování ovládacího prvku Windows Forms.

## <a name="syntax"></a>Syntaxe

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>Parametry

*Ovládací prvek TManagedControl*<br/>
Ovládací prvek .NET Framework Windows Forms, který se zobrazí v aplikaci knihovny MFC.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CWinFormsControl::Ovládací prvek CWinFormsControl](#cwinformscontrol)|Vytvoří objekt obálky ovládacího prvku MFC Windows Forms.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Vytvoří ovládací prvek Windows Forms v kontejneru knihovny MFC.|
|[Ovládací prvek CWinFormsControl::Ovládací prvek GetControl](#getcontrol)|Načte ukazatel na ovládací prvek Windows Forms.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Načte popisovač do ovládacího prvku Windows Forms.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CWinFormsControl::operátor -&gt;](#operator_-_gt)|Nahradí [cWinFormsControl::GetControl](#getcontrol) ve výrazech.|
|[CWinFormsControl::operátor TManagedControl^](#operator_tmanagedcontrol)|Přetypování typu jako ukazatel ovládacího prvku Windows Forms.|

## <a name="remarks"></a>Poznámky

Třída `CWinFormsControl` poskytuje základní funkce pro hostování ovládacího prvku Windows Forms.

Další informace o používání formulářů Systému Windows naleznete [v tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Kód knihovny MFC by neměl ukládat `m_hWnd`popisovače okna do mezipaměti (obvykle uložené v ). Některé vlastnosti ovládacího prvku Windows `Window` Forms vyžadují, aby `DestroyWindow` `CreateWindow`základní win32 být zničena a znovu vytvořena pomocí a . MFC Windows Forms implementace `Destroy` zpracovává `Create` a události ovládacích `m_hWnd` prvků aktualizovat člena.

> [!NOTE]
> Integrace mfc Windows Forms funguje pouze v projektech, které dynamicky propojují s knihovnou MFC (ve které je definována knihovna AFXDLL).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h

## <a name="cwinformscontrolcreatemanagedcontrol"></a><a name="createmanagedcontrol"></a>CWinFormsControl::CreateManagedControl

Vytvoří ovládací prvek Windows Forms v kontejneru knihovny MFC.

```
inline BOOL CreateManagedControl(
    System::Type^ pType,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID)
inline BOOL CreateManagedControl(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);

inline BOOL CreateManagedControl(
    DWORD dwStyle,
    int nPlaceHolderID,
    CWnd* pParentWnd);

inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);
```

### <a name="parameters"></a>Parametry

*pTyp*<br/>
Datový typ ovládacího prvku, který má být vytvořen. Musí být [datový typ.](/dotnet/api/system.type)

*dwStyl*<br/>
Styl okna, který se má použít pro ovládací prvek. Zadejte kombinaci [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). V současné době jsou podporovány pouze následující styly: WS_TABSTOP, WS_VISIBLE, WS_DISABLED a WS_GROUP.

*Rect*<br/>
[Rect struktura,](/windows/win32/api/windef/ns-windef-rect) která definuje souřadnice levého horního a pravého dolního rohu ovládacího prvku (pouze první přetížení).

*nPlaceHolderID*<br/>
Popisovač statického ovládacího prvku zástupného místa umístěného v Editoru prostředků. Nově vytvořený ovládací prvek Windows Forms nahradí statický ovládací prvek za předpokladu, že jeho umístění, pořadí vykreslování a styly (pouze druhé přetížení).

*pParentWnd*<br/>
Ukazatel na nadřazené okno.

*Nid*<br/>
Číslo ID prostředku, které má být přiřazeno nově vytvořenému ovládacímu prvku.

*pOvládací prvek*<br/>
Instance ovládacího prvku Windows Forms, který má být přidružen k objektu [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) (pouze čtvrté přetížení).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí nenulovou hodnotu. Pokud neúspěšné vrátí nula.

### <a name="remarks"></a>Poznámky

Tato metoda inkonzisuje ovládací prvek .NET Framework Windows Forms v kontejneru knihovny MFC.

První přetížení metody přijímá datový typ rozhraní .NET Framework *pType* tak, aby knihovna MFC může vytvořit instanci nového objektu tohoto typu. *pType* musí být [datový](/dotnet/api/system.type) typ typu.

Druhé přetížení metody vytvoří ovládací prvek Windows `TManagedControl` Forms na `CWinFormsControl` základě parametru šablony třídy. Velikost a umístění ovládacího prvku `RECT` je založena na struktuře předané metodě. Pouze *dwStyle* záležitosti pro styly.

Třetí přetížení metody vytvoří ovládací prvek Windows Forms, který nahradí statický ovládací prvek, jeho zničení a za předpokladu, že jeho umístění, pořadí vykreslování a styly. Statický ovládací prvek slouží pouze jako zástupný symbol pro ovládací prvek Windows Forms. Při vytváření ovládacího prvku toto přetížení kombinuje styly z *dwStyle* se styly prostředků statického ovládacího prvku.

Čtvrté přetížení metody umožňuje předat v již instance ovládacího prvku Windows Forms *pControl,* který knihovna MFC zabalí. Musí být stejného typu `TManagedControl` jako parametr `CWinFormsControl` šablony třídy.

Ukázky při použití ovládacích prvků formuláře [systému Windows naleznete v tématu Použití uživatelského ovládacího prvku formuláře systému Windows v knihovně MFC.](../../dotnet/using-a-windows-form-user-control-in-mfc.md)

## <a name="cwinformscontrolcwinformscontrol"></a><a name="cwinformscontrol"></a>CWinFormsControl::Ovládací prvek CWinFormsControl

Vytvoří objekt obálky ovládacího prvku MFC Windows Forms.

```
CWinFormsControl();
```

### <a name="remarks"></a>Poznámky

Ovládací prvek Windows Forms je instancepři volání [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrol"></a><a name="getcontrol"></a>Ovládací prvek CWinFormsControl::Ovládací prvek GetControl

Načte ukazatel na ovládací prvek Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na ovládací prvek Windows Forms.

### <a name="example"></a>Příklad

  Viz [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsControl::GetControlHandle

Načte popisovač do ovládacího prvku Windows Forms.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač ovládacího prvku Windows Forms.

### <a name="remarks"></a>Poznámky

`GetControlHandle`je pomocná metoda, která vrací popisovač okna uložený ve vlastnostech ovládacího prvku rozhraní .NET Framework. Hodnota popisovače okna je zkopírována do [CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) během volání [CWnd::Attach](../../mfc/reference/cwnd-class.md#attach).

## <a name="cwinformscontroloperator--gt"></a><a name="operator_-_gt"></a>CWinFormsControl::operátor -&gt;

Nahradí [cWinFormsControl::GetControl](#getcontrol) ve výrazech.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Poznámky

Tento operátor poskytuje pohodlnou `GetControl` syntaxi, která nahrazuje ve výrazech.

Další informace o formulářích Windows naleznete v [tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformscontroloperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol"></a>CWinFormsControl::operátor TManagedControl^

Přetypování typu jako ukazatel ovládacího prvku Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Poznámky

Tento operátor `CWinFormsControl<TManagedControl>` předá funkce, které přijímají ukazatel na ovládací prvek Windows Forms.

## <a name="see-also"></a>Viz také

[Třída CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)<br/>
[Třída CWinFormsView](../../mfc/reference/cwinformsview-class.md)
