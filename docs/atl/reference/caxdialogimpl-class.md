---
title: CAxDialogImpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
dev_langs:
- C++
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a22b04bd0a362824e20621eaa7f66cafd0e55cf5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024499"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl – třída

Tato třída implementuje dialog (modálním nebo nemodálním), který je hostitelem ovládacích prvků ActiveX.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `CAxDialogImpl`.

*Tčíslice*<br/>
Okno základní třída pro `CDialogImplBaseT`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Volání této metody vytvoříte nebo zrušíte avízo o všech položek v mapě událostí jímky mapování objektu.|
|[CAxDialogImpl::Create](#create)|Volejte tuto metodu za účelem vytvoření nemodálního dialogového okna.|
|[CAxDialogImpl::DestroyWindow](#destroywindow)|Voláním této metody lze zničit nemodální dialogové okno.|
|[CAxDialogImpl::DoModal](#domodal)|Volejte tuto metodu za účelem vytvoření modálního dialogového okna.|
|[CAxDialogImpl::EndDialog](#enddialog)|Voláním této metody lze zničit modální dialogové okno.|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Volejte tuto metodu za účelem získání ukazatel `DialogProc` funkce zpětného volání.|
|[CAxDialogImpl::GetIDD](#getidd)|Volání této metody k získání ID prostředku šablony dialogového okna|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Volat tuto metodu za účelem určení, zda zpráva je určený pro toto dialogové okno a pokud se jedná, zprávu zpracovat.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAxDialogImpl::m_bModal](#m_bmodal)|Proměnná, která existuje pouze v ladění sestavení a je nastavená na hodnotu true, pokud je modální dialogové okno.|

## <a name="remarks"></a>Poznámky

`CAxDialogImpl` Umožňuje vytvořit modální a nemodální dialogové okno. `CAxDialogImpl` poskytuje pole proceduru dialogového okna, který používá výchozí mapování zpráv ke směrování zpráv do příslušné obslužné rutiny.

`CAxDialogImpl` je odvozen od `CDialogImplBaseT`, která je dále odvozeno z *Tčíslice* (ve výchozím nastavení, `CWindow`) a `CMessageMap`.

Vaše třída musí definovat člen typu IDD, který určuje ID prostředku šablony dialogového okna. Příkladem je přidání objektu pomocí dialogového okna ATL **přidat třídu** dialogové okno automaticky přidá do třídy následující řádek:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

kde `MyDialog` je **krátký název** zadaný v Průvodce dialogem ATL.

Zobrazit [implementace dialogového okna](../../atl/implementing-a-dialog-box.md) Další informace.

Všimněte si, že ovládací prvek ActiveX na modální dialogové okno vytvořené s `CAxDialogImpl` nebude podporovat přístupové klávesy. Pro podporu klávesové zkratky v dialogovém okně vytvořené pomocí `CAxDialogImpl`, nemodální dialogové okno vytvořit a smyčku zpráv, pomocí [CAxDialogImpl::IsDialogMessage](#isdialogmessage) po získání zprávu z fronty pro zpracování přístupová klávesa.

Další informace o `CAxDialogImpl`, naleznete v tématu [ATL – ovládací prvek členství ve skupině nejčastější dotazy k](../../atl/atl-control-containment-faq.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cmessagemap –](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="advisesinkmap"></a>  CAxDialogImpl::AdviseSinkMap

Volání této metody vytvoříte nebo zrušíte avízo o všech položek v mapě událostí jímky mapování objektu.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
Nastavte na hodnotu true, pokud mají všechny položky jímky doporučujeme; jímka hodnotu false, pokud všechny položky jsou unadvised.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="create"></a>  CAxDialogImpl::Create

Volejte tuto metodu za účelem vytvoření nemodálního dialogového okna.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
[in] Popisovač nadřazenému oknu.

*dwInitParam*<br/>
[in] Určuje hodnotu pro předání do dialogového okna aplikace *lParam* parametr nezavěsíte zprávu.

*RECT – &AMP;*<br/>
Tento parametr není používán. Tento parametr je předán `CComControl`.

### <a name="return-value"></a>Návratová hodnota

Popisovač do nově vytvořeného dialogových oken.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je automaticky připojen k `CAxDialogImpl` objektu. Chcete-li vytvořit modální dialogové okno, zavolejte [DoModal](#domodal).

Druhý přepsání je k dispozici pouze proto dialogová okna je možné s [ccomcontrol –](../../atl/reference/ccomcontrol-class.md).

##  <a name="destroywindow"></a>  CAxDialogImpl::DestroyWindow

Voláním této metody lze zničit nemodální dialogové okno.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud v okně je úspěšně zničen; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Nevolejte `DestroyWindow` ke zničení modální dialogové okno. Volání [EndDialog](#enddialog) místo.

##  <a name="domodal"></a>  CAxDialogImpl::DoModal

Volejte tuto metodu za účelem vytvoření modálního dialogového okna.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
[in] Popisovač nadřazenému oknu. Výchozí hodnota je vrácená hodnota [GetActiveWindow](https://msdn.microsoft.com/library/windows/desktop/ms646292) funkci Win32.

*dwInitParam*<br/>
[in] Určuje hodnotu pro předání do dialogového okna aplikace *lParam* parametr nezavěsíte zprávu.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu se hodnota *nRetCode* parametr zadaný ve volání [EndDialog](#enddialog); v opačném případě hodnota -1.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je automaticky připojen k `CAxDialogImpl` objektu.

Vytvoří nemodální dialogové okno, voláním [vytvořit](#create).

##  <a name="enddialog"></a>  CAxDialogImpl::EndDialog

Voláním této metody lze zničit modální dialogové okno.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
[in] Hodnota, která má být vrácen [DoModal](#domodal).

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud jeho zničení dialogových oken; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

`EndDialog` je nutné volat pomocí pole proceduru dialogového okna. Po zničení dialogových oken Windows používá hodnotu *nRetCode* jako návratovou hodnotu pro `DoModal`, který vytvoří dialogové okno.

> [!NOTE]
>  Nevolejte `EndDialog` ke zničení nemodální dialogové okno. Volání [destroywindow –](#destroywindow) místo.

##  <a name="getdialogproc"></a>  CAxDialogImpl::GetDialogProc

Volejte tuto metodu za účelem získání ukazatel `DialogProc` funkce zpětného volání.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel `DialogProc` funkce zpětného volání.

### <a name="remarks"></a>Poznámky

`DialogProc` Funkce je funkce zpětného volání definované aplikací.

##  <a name="getidd"></a>  CAxDialogImpl::GetIDD

Volání této metody k získání ID prostředku šablony dialogového okna.

```
int GetIDD();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ID prostředku šablony dialogového okna.

##  <a name="isdialogmessage"></a>  CAxDialogImpl::IsDialogMessage

Volat tuto metodu za účelem určení, zda zpráva je určený pro toto dialogové okno a pokud se jedná, zprávu zpracovat.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Ukazatel [MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958) strukturu, která obsahuje zprávy, která se má zkontrolovat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud zpráva byla zpracovaných, FALSE, jinak.

### <a name="remarks"></a>Poznámky

Tato metoda je určena k volání z v rámci smyčky zpráv.

##  <a name="m_bmodal"></a>  CAxDialogImpl::m_bModal

Proměnná, která existuje pouze v ladění sestavení a je nastavená na hodnotu true, pokud je modální dialogové okno.

```
bool m_bModal;
```

## <a name="see-also"></a>Viz také

[CDialogImpl – třída](../../atl/reference/cdialogimpl-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
