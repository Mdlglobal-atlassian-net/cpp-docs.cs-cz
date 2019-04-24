---
title: CWinFormsDialog – třída
ms.date: 03/27/2019
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
ms.openlocfilehash: 1542f852a8fe3f05d81ae59efb8a522caae671fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323408"
---
# <a name="cwinformsdialog-class"></a>CWinFormsDialog – třída

Obálka pro třídu dialogového okna knihovny MFC, který je hostitelem uživatelského ovládacího prvku Windows Forms.

## <a name="syntax"></a>Syntaxe

```
template <typename TManagedControl>
class CWinFormsDialog :
    public CDialog
```

#### <a name="parameters"></a>Parametry

*TManagedControl*<br/>
Rozhraní .NET Framework uživatelský ovládací prvek zobrazený v aplikaci knihovny MFC.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Vytvoří `CWinFormsDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWinFormsDialog::GetControl](#getcontrol)|Získá odkaz na uživatelský ovládací prvek Windows Forms.|
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Načte popisovač okna do uživatelského ovládacího prvku Windows Forms.|
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Vytváření a hostování uživatelského ovládacího prvku Windows Forms v něm inicializuje v dialogovém okně knihovny MFC.|

### <a name="public-operators"></a>Veřejné operátory

|Název||
|----------|-|
|[CWinFormsDialog::operator-&gt;](#operator_-_gt)|Nahradí [CWinFormsDialog::GetControl](#getcontrol) ve výrazech.|
|[CWinFormsDialog::operator TManagedControl^](#operator-tmanagedcontrol-hat)|Přetypování typu jako odkaz na uživatelský ovládací prvek Windows Forms.|

## <a name="remarks"></a>Poznámky

`CWinFormsDialog` je obálka pro třídu dialogového okna knihovny MFC ( [CDialog](../../mfc/reference/cdialog-class.md)), který je hostitelem uživatelského ovládacího prvku Windows Forms. To umožňuje zobrazit ovládací prvky rozhraní .NET Framework v modálním nebo nemodálním dialogovém okně knihovny MFC.

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) a [hostitelské poskytování uživatelského Windows Form jako dialogového okna knihovny MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h

##  <a name="cwinformsdialog"></a>  CWinFormsDialog::CWinFormsDialog

Vytvoří `CWinFormsDialog` objektu.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>Parametry

*nIDTemplate*<br/>
Obsahuje ID prostředku šablony dialogového okna pole. Použití editoru dialogového okna můžete vytvořit šablony dialogového okna a uložit do souboru skriptu prostředků aplikace. Další informace o šablonách dialogového okna, naleznete v tématu [CDialog – třída](../../mfc/reference/cdialog-class.md).

##  <a name="getcontrol"></a>  CWinFormsDialog::GetControl

Získá odkaz na uživatelský ovládací prvek Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na ovládacím prvku Windows Forms v dialogovém okně knihovny MFC.

##  <a name="getcontrolhandle"></a>  CWinFormsDialog::GetControlHandle

Načte popisovač okna do uživatelského ovládacího prvku Windows Forms.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač okna do uživatelského ovládacího prvku Windows Forms.

##  <a name="oninitdialog"></a>  CWinFormsDialog::OnInitDialog

Vytváření a hostování uživatelského ovládacího prvku Windows Forms v něm inicializuje v dialogovém okně knihovny MFC.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota určující, zda v aplikaci je nastaven vstupní fokus na některý ovládací prvky v dialogovém okně. Pokud `OnInitDialog` vrátí nenulovou hodnotu, Windows nastaví zaměření pro vstup na první prvek v dialogovém okně. Tato metoda může vrátit 0 pouze v případě, že v aplikaci je v dialogovém okně explicitně nastaven vstupní fokus na některý ovládací prvky.

### <a name="remarks"></a>Poznámky

Když je vytvořena v dialogovém okně knihovny MFC (pomocí [vytvořit](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect), nebo [DoModal](../../mfc/reference/cdialog-class.md#domodal) metody zděděné z [CDialog](../../mfc/reference/cdialog-class.md)), WM_ Odeslání zprávy INITDIALOG a tato metoda je volána. Vytvoří instanci ovládacího prvku Windows Forms v dialogovém okně a velikost dialogového okna tak, aby vyhovovaly velikosti uživatelského ovládacího prvku. Potom hostitelem nového ovládacího prvku v dialogovém okně knihovny MFC.

Tato členská funkce přepište, pokud je třeba provést zvláštní zpracování při inicializaci dialogových oken. Další informace o použití této metody naleznete v tématu [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).

##  <a name="operator_-_gt"></a>  CWinFormsDialog::operator-&gt;

Nahradí [CWinFormsDialog::GetControl](#getcontrol) ve výrazech.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor poskytuje pohodlné syntaxe, která nahrazuje `GetControl` ve výrazech.

Informace o používání formulářů Windows najdete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator-tmanagedcontrol-hat"></a>  CWinFormsDialog::operator TManagedControl ^

Přetypování typu jako odkaz na uživatelský ovládací prvek Windows Forms.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor přetypování typu jako odkaz na ovládacím prvku Windows Forms. Slouží k předání `CWinFormsDialog<TManagedControl>` dialogové okno funkce, které přijímají ukazatel na objekt ovládacího prvku Windows Forms uživatele.

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CWinFormsView – třída](../../mfc/reference/cwinformsview-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
