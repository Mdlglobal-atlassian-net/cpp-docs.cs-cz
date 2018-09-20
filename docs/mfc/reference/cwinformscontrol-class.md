---
title: CWinFormsControl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 57a06fe87e7d4fbcf698cc333022c4c32afb40da
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442601"
---
# <a name="cwinformscontrol-class"></a>CWinFormsControl – třída

Poskytuje základní funkce pro hostování ovládacího prvku Windows Forms.

## <a name="syntax"></a>Syntaxe

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>Parametry

*TManagedControl*<br/>
Ovládací prvek formulářů Windows rozhraní .NET Framework zobrazeného v aplikaci knihovny MFC.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Vytvoří objekt obálky ovládacího prvku Windows Forms knihovny MFC.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Vytvoří ovládacího prvku Windows Forms v MFC kontejneru.|
|[CWinFormsControl::GetControl](#getcontrol)|Načte ukazatel na ovládacím prvku Windows Forms.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Načte popisovač na ovládacím prvku Windows Forms.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CWinFormsControl::operator-&gt;](#operator_-_gt)|Nahradí [CWinFormsControl::GetControl](#getcontrol) ve výrazech.|
|[CWinFormsControl::operator TManagedControl ^](#operator_tmanagedcontrol)|Přetypování typu jako ukazatel na ovládacím prvku Windows Forms.|

## <a name="remarks"></a>Poznámky

`CWinFormsControl` Třída poskytuje základní funkce pro hostování ovládacího prvku Windows Forms.

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Kódu knihovny MFC by neměly ukládat do mezipaměti okno obslužné rutiny (obvykle ukládají do `m_hWnd`). Některé vlastnosti ovládacího prvku Windows Forms, který vyžaduje základní Win32 `Window` být zrušen a znovu vytvořit pomocí `DestroyWindow` a `CreateWindow`. Obslužné rutiny implementace MFC Windows Forms `Destroy` a `Create` událostí ovládacích prvků aktualizovat `m_hWnd` člena.

> [!NOTE]
>  Integrace formulářů Windows MFC funguje jenom v projektech, které dynamicky propojit s knihovnou MFC (ve kterém je definována AFXDLL).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h

##  <a name="createmanagedcontrol"></a>  CWinFormsControl::CreateManagedControl

Vytvoří ovládacího prvku Windows Forms v MFC kontejneru.

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
Datový typ ovládacího prvku, který má být vytvořen. Musí být [typ](https://msdn.microsoft.com/library/system.type) datového typu.

*dwStyle*<br/>
Styl okna pro ovládací prvek. Určuje kombinaci [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). V současné době jsou podporovány pouze následující styly: WS_TABSTOP, WS_VISIBLE, WS_DISABLED a WS_GROUP.

*Rect*<br/>
A [Rect – struktura](../../mfc/reference/rect-structure1.md) , který definuje souřadnice levého a pravého dolního rohu ovládacího prvku (první přetížení pouze).

*nPlaceHolderID*<br/>
Obslužná rutina ovládacího prvku držitel statické místo umístěné v editoru prostředků. Nově vytvořený ovládací prvek Windows Forms nahradí statický ovládací prvek, za předpokladu, že jeho umístění, pořadí vykreslování a styly (druhé přetížení pouze).

*pParentWnd*<br/>
Ukazatel do nadřazeného okna.

*nID*<br/>
Číslo ID prostředků má být přiřazena k nově vytvořený ovládací prvek.

*pControl*<br/>
Instance ovládacího prvku Windows Forms přidruženo [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) objekt (pouze čtvrtý přetížení).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí nenulovou hodnotu. Pokud není úspěšné, vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří instanci ovládacího prvku formulářů Windows rozhraní .NET Framework v kontejneru prvku knihovny MFC.

První přetížení metody přijímá datový typ rozhraní .NET Framework *pType* tak, aby MFC instanci můžete vytvořit nový objekt tohoto typu. *pType* musí být [typ](https://msdn.microsoft.com/library/system.type) datového typu.

Druhé přetížení metody vytvoří ovládacího prvku Windows Forms na základě `TManagedControl` parametrem šablony `CWinFormsControl` třídy. Podle velikosti a pozice ovládacího prvku `RECT` předané metodě. Pouze *dwStyle* je důležité pro styly.

Třetí přetížení metody vytvoří ovládací prvek Windows Forms, který nahrazuje statický ovládací prvek, došlo k jeho zničení a za předpokladu, že jeho umístění, pořadí vykreslování a styly. Statický ovládací prvek slouží pouze jako zástupný symbol pro ovládací prvek Windows Forms. Při vytváření ovládacího prvku, toto přetížení kombinuje styly z *dwStyle* se styly prostředků statický ovládací prvek.

Čtvrtý přetížení metody umožňuje předat v ovládacím prvku Windows Forms už vytvořenou instanci *pControl* , která se zalomí knihovny MFC. Musí být stejného typu jako `TManagedControl` parametrem šablony `CWinFormsControl` třídy.

Zobrazit [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) ve formuláři Windows ukázky pro ovládací prvky.

##  <a name="cwinformscontrol"></a>  CWinFormsControl::CWinFormsControl

Vytvoří objekt obálky ovládacího prvku Windows Forms knihovny MFC.

```
CWinFormsControl();
```

### <a name="remarks"></a>Poznámky

Při volání je vytvořena instance ovládacího prvku Windows Forms [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

##  <a name="getcontrol"></a>  CWinFormsControl::GetControl

Načte ukazatel na ovládacím prvku Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na ovládacím prvku Windows Forms.

### <a name="example"></a>Příklad

  Zobrazit [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

##  <a name="getcontrolhandle"></a>  CWinFormsControl::GetControlHandle

Načte popisovač na ovládacím prvku Windows Forms.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač do ovládacího prvku Windows Forms.

### <a name="remarks"></a>Poznámky

`GetControlHandle` je pomocná metoda, která vrací popisovač okna uložená ve vlastnosti ovládacího prvku rozhraní .NET Framework. Hodnota popisovače okna je zkopírován do [CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) během volání [CWnd::Attach](../../mfc/reference/cwnd-class.md#attach).

##  <a name="operator_-_gt"></a>  CWinFormsControl::operator-&gt;

Nahradí [CWinFormsControl::GetControl](#getcontrol) ve výrazech.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Poznámky

Tento operátor poskytuje pohodlné syntaxe, která nahrazuje `GetControl` ve výrazech.

Další informace o Windows Forms, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_tmanagedcontrol"></a>  CWinFormsControl::operator TManagedControl ^

Přetypování typu jako ukazatel na ovládacím prvku Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Poznámky

Tento operátor předá `CWinFormsControl<TManagedControl>` na funkce, které přijímají ukazatel na ovládacím prvku Windows Forms.

## <a name="see-also"></a>Viz také

[CWinFormsDialog – třída](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView – třída](../../mfc/reference/cwinformsview-class.md)
