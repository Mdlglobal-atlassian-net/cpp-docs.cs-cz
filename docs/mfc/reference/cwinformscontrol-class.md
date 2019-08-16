---
title: CWinFormsControl – třída
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
ms.openlocfilehash: 75a6d7ea2b4f3ab229d7e3f4d411711261bb1b82
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502194"
---
# <a name="cwinformscontrol-class"></a>CWinFormsControl – třída

Poskytuje základní funkce pro hostování model Windows Formsho ovládacího prvku.

## <a name="syntax"></a>Syntaxe

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>Parametry

*TManagedControl*<br/>
.NET Framework model Windows Forms ovládací prvek, který se má zobrazit v aplikaci MFC.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Vytvoří objekt obálky ovládacího prvku MFC model Windows Forms.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Vytvoří ovládací prvek model Windows Forms v kontejneru MFC.|
|[CWinFormsControl::GetControl](#getcontrol)|Načte ukazatel na ovládací prvek model Windows Forms.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Načte popisovač ovládacího prvku model Windows Forms.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CWinFormsControl:: operator-&gt;](#operator_-_gt)|Nahradí [CWinFormsControl:: GetControl](#getcontrol) ve výrazech.|
|[CWinFormsControl:: operator TManagedControl ^](#operator_tmanagedcontrol)|Přetypování typu jako ukazatele na ovládací prvek model Windows Forms.|

## <a name="remarks"></a>Poznámky

`CWinFormsControl` Třída poskytuje základní funkce pro hostování model Windows Formsho ovládacího prvku.

Další informace o použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Váš kód knihovny MFC by neměl ukládat popisovače okna do mezipaměti ( `m_hWnd`obvykle se ukládají v). Některé vlastnosti ovládacího prvku model Windows Forms vyžadují, aby byl `Window` základní Win32 zničen a znovu vytvořen pomocí `DestroyWindow` a `CreateWindow`. Model Windows Forms implementace knihovny MFC zpracovává `Destroy` události a `Create` ovládacích prvků k aktualizaci `m_hWnd` člena.

> [!NOTE]
>  Knihovna MFC model Windows Forms Integration funguje pouze v projektech, které jsou propojeny dynamicky s knihovnou MFC (ve které je definována AFXDLL –).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms. h

##  <a name="createmanagedcontrol"></a>  CWinFormsControl::CreateManagedControl

Vytvoří ovládací prvek model Windows Forms v kontejneru MFC.

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

*pType*<br/>
Datový typ ovládacího prvku, který má být vytvořen. Musí se jednat o [typ](/dotnet/api/system.type) datový typ.

*dwStyle*<br/>
Styl okna, který se má použít pro ovládací prvek Určete kombinaci [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). V současné době jsou podporovány pouze následující styly: WS_TABSTOP, WS_VISIBLE, WS_DISABLED a WS_GROUP.

*OBD*<br/>
[Struktura Rect](/windows/win32/api/windef/ns-windef-rect) definující souřadnice levého horního a pravého dolního rohu ovládacího prvku (pouze první přetížení).

*nPlaceHolderID*<br/>
Popisovač ovládacího prvku zástupce statického místa umístěný v editoru prostředků Nově vytvořený ovládací prvek model Windows Forms nahradí statický ovládací prvek za předpokladu, že jeho poloha, pořadí vykreslování a styly (pouze druhé přetížení).

*pParentWnd*<br/>
Ukazatel na nadřazené okno.

*nID*<br/>
Číslo ID prostředku, které má být přiřazeno nově vytvořenému ovládacímu prvku.

*pControl*<br/>
Instance ovládacího prvku model Windows Forms, který se má přidružit k objektu [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) (jenom čtvrté přetížení).

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí nenulovou hodnotu. V případě neúspěchu vrátí hodnotu nula.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří instanci ovládacího prvku .NET Framework model Windows Forms v kontejneru MFC.

První přetížení metody přijímá .NET Framework datový typ *pType* , aby mohla knihovna MFC vytvořit instance nového objektu tohoto typu. *pType* musí být datový typ [Type](/dotnet/api/system.type) .

Druhé přetížení metody vytvoří ovládací prvek model Windows Forms v závislosti na `TManagedControl` parametru `CWinFormsControl` šablony třídy. Velikost a poloha ovládacího prvku jsou založeny na `RECT` struktuře předané metodě. Pouze *dwStyleé* záležitosti pro styly.

Třetí přetížení metody vytvoří ovládací prvek model Windows Forms, který nahradí statický ovládací prvek, zničí ho a za předpokladu, že se jedná o pozici, pořadí vykreslování a styly. Statický ovládací prvek slouží pouze jako zástupný symbol pro ovládací prvek model Windows Forms. Při vytváření ovládacího prvku kombinuje toto přetížení styly z *dwStyle* se styly prostředků statického ovládacího prvku.

Čtvrté přetížení metody umožňuje předat již vytvořenou instanci model Windows Forms ovládacího prvku *pControl* , kterou bude knihovna MFC zabalit. Musí být stejného typu jako `TManagedControl` parametr `CWinFormsControl` šablony třídy.

Ukázky použití ovládacích prvků Windows Form naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) .

##  <a name="cwinformscontrol"></a>CWinFormsControl::CWinFormsControl

Vytvoří objekt obálky ovládacího prvku MFC model Windows Forms.

```
CWinFormsControl();
```

### <a name="remarks"></a>Poznámky

Při volání [CWinFormsControl:: CreateManagedControl](#createmanagedcontrol)se vytvoří instance ovládacího prvku model Windows Forms.

##  <a name="getcontrol"></a>CWinFormsControl:: GetControl

Načte ukazatel na ovládací prvek model Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na ovládací prvek model Windows Forms.

### <a name="example"></a>Příklad

  Viz [CWinFormsControl:: CreateManagedControl](#createmanagedcontrol).

##  <a name="getcontrolhandle"></a>CWinFormsControl::GetControlHandle

Načte popisovač ovládacího prvku model Windows Forms.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač ovládacího prvku model Windows Forms.

### <a name="remarks"></a>Poznámky

`GetControlHandle`je pomocná metoda, která vrací popisovač okna uložený ve vlastnostech ovládacího prvku .NET Framework. Hodnota popisovače okna je zkopírována do [CWnd:: m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) během volání [CWnd:: Attach](../../mfc/reference/cwnd-class.md#attach).

##  <a name="operator_-_gt"></a>CWinFormsControl:: operator-&gt;

Nahradí [CWinFormsControl:: GetControl](#getcontrol) ve výrazech.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Poznámky

Tento operátor poskytuje pohodlný syntax, která nahrazuje `GetControl` výrazy.

Další informace o model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_tmanagedcontrol"></a>CWinFormsControl:: operator TManagedControl ^

Přetypování typu jako ukazatele na ovládací prvek model Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Poznámky

Tento operátor předává `CWinFormsControl<TManagedControl>` funkci, která přijímá ukazatel na ovládací prvek model Windows Forms.

## <a name="see-also"></a>Viz také:

[CWinFormsDialog – třída](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView – třída](../../mfc/reference/cwinformsview-class.md)
