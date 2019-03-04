---
title: 'TN001: Registrace tříd oken'
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: 68c851ae6a6b1b8578df90e2618f257122797aa5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294145"
---
# <a name="tn001-window-class-registration"></a>TN001: Registrace tříd oken

Tato poznámka popisuje rutiny knihovny MFC, které registrují zvláštní [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa)es vyžadované Microsoft Windows. Konkrétní `WNDCLASS` jsou uvedeny atributy použité v rámci MFC a Windows.

## <a name="the-problem"></a>Problém

Atributy [CWnd](../mfc/reference/cwnd-class.md) objektů, jako je třeba `HWND` zpracování ve Windows, jsou uložená na dvou místech: objekt okna a `WNDCLASS`. Název `WNDCLASS` předána pro okno Obecné vytváření funkcí, jako [CWnd::Create](../mfc/reference/cwnd-class.md#create) a [CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create) v *lpszClassName* parametru.

To `WNDCLASS` musí být registrovány prostřednictvím jednoho z 4 způsoby:

- Implicitně pomocí MFC poskytuje `WNDCLASS`.

- Implicitně pomocí vytvoření podtřídy ovládacího prvku Windows (nebo jiný ovládací prvek).

- Explicitně voláním knihovny MFC [afxregisterwndclass –](../mfc/reference/application-information-and-management.md#afxregisterwndclass) nebo [afxregisterclass –](../mfc/reference/application-information-and-management.md#afxregisterclass).

- Explicitně voláním rutiny Windows [RegisterClass](/windows/desktop/api/winuser/nf-winuser-registerclassa).

## <a name="wndclass-fields"></a>WNDCLASS pole

`WNDCLASS` Struktura se skládá z různých polí, které popisují třídy okna. Následující tabulka zobrazuje pole a určuje, jak se používají v aplikacích MFC:

|Pole|Popis|
|-----------|-----------------|
|*lpfnWndProc*|proces okna musí být `AfxWndProc`|
|*cbClsExtra*|nepoužívá se (musí být nula)|
|*cbWndExtra*|nepoužívá se (musí být nula)|
|*hInstance*|automaticky vyplněno [afxgetinstancehandle –](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|Níže jsou uvedeny ikonu oken s rámečkem|
|*hCursor*|Níže jsou uvedeny kurzor když je okno, myš|
|*hbrBackground*|Barva pozadí, najdete níže|
|*lpszMenuName*|nepoužívá se (by měl mít hodnotu NULL)|
|*lpszClassName*|Název třídy, viz níže|

## <a name="provided-wndclasses"></a>K dispozici WNDCLASSes

Dřívější verze knihovny MFC (před MFC 4.0), poskytují několik předdefinovaných tříd oken. Tyto třídy okna jsou už k dispozici ve výchozím nastavení. Aplikace by měly používat `AfxRegisterWndClass` s příslušnými parametry.

Pokud aplikace poskytuje prostředek s ID zadaného prostředku (například AFX_IDI_STD_FRAME), použije MFC tohoto prostředku. Jinak se bude používat výchozí prostředek. Ikony je použita ikona standardní aplikace a pro kurzor, se používá standardní šipka kurzoru.

Dvě ikony podporují aplikace MDI s typy jednotlivý dokument: jednu ikonu pro hlavní aplikaci, na ikonu pro ikonickým dokument/MDIChild windows. Pro více typů dokumentů s jinou ikonami, je nutné zaregistrovat Další `WNDCLASS`no nebo použití [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) funkce.

`CFrameWnd::LoadFrame` k registraci `WNDCLASS` pomocí ID ikony je zadat jako první parametr a standardní následující atributy:

- styl třídy: CS_DBLCLKS &AMP;#124; CS_HREDRAW &AMP;#124; CS_VREDRAW;

- icon AFX_IDI_STD_FRAME

- šipka kurzoru

- Barva pozadí COLOR_WINDOW

Hodnoty pro barvu pozadí a kurzor [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) nepoužívají od klientské oblasti `CMDIFrameWnd` zcela se vztahuje **MDICLIENT** okno. Společnost Microsoft nedoporučuje vytváření podtříd **MDICLIENT** okno tedy použít standardní barvy a typy kurzorů, pokud je to možné.

## <a name="subclassing-and-superclassing-controls"></a>Vytváření podtříd a Superclassing ovládacích prvků

Pokud je podtřídou nebo nadřazené třídy Windows (například [CButton](../mfc/reference/cbutton-class.md)) pak automaticky získá vaše třída `WNDCLASS` atributů uvedený v implementaci Windows ovládacího prvku.

## <a name="the-afxregisterwndclass-function"></a>Afxregisterwndclass – funkce

Knihovna MFC poskytuje pomocné funkce pro registraci třídy okna. Vzhledem k sadě atributů (styl třídy okna, kurzor, štětec pozadí a ikonu), vygeneruje se syntetické název a výsledné třídy okna je zaregistrovaný. Například

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

Tato funkce vrací řetězec dočasný název třídy generované registrované okna. Další informace o této funkci najdete v tématu [afxregisterwndclass –](../mfc/reference/application-information-and-management.md#afxregisterwndclass).

Vrácený řetězec je dočasný ukazatel do vyrovnávací paměti statický řetězec. To platí až do příštího volání metody `AfxRegisterWndClass`. Pokud chcete zachovat tento řetězec kolem, uložte ho v [CString](../atl-mfc-shared/using-cstring.md) proměnné, jako v následujícím příkladu:

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass` vyvolá výjimku [cresourceexception –](../mfc/reference/cresourceexception-class.md) Pokud třídu okna se nepodařilo zaregistrovat (z důvodu nesprávných parametrů, nebo nedostatek paměti Windows).

## <a name="the-registerclass-and-afxregisterclass-functions"></a>RegisterClass a afxregisterclass – funkce

Pokud chcete udělat nic víc propracovaných než co `AfxRegisterWndClass` poskytuje, můžete volat rozhraní API Windows `RegisterClass` nebo funkce MFC `AfxRegisterClass`. `CWnd`, [CFrameWnd](../mfc/reference/cframewnd-class.md) a [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create` funkce přijímají *lpszClassName* název řetězce pro třídu okna jako první parametr. Můžete použít jakýkoli název třídy okna registrované, bez ohledu na metodu, kterou jste použili k registraci ho.

Je důležité používat `AfxRegisterClass` (nebo `AfxRegisterWndClass`) v knihovně DLL v systému Win32. Win32 nelze zrušit registraci automaticky třídy registrovaných knihovny DLL, proto musí explicitně zrušit registraci třídy při ukončení knihovny DLL. S použitím `AfxRegisterClass` místo `RegisterClass` to se automaticky udělá za vás. `AfxRegisterClass` udržuje seznam jedinečných tříd registrovaných vaši knihovnu DLL a automaticky zruší registraci je při ukončení knihovny DLL. Při použití `RegisterClass` v knihovně DLL, ujistěte se, že jsou všechny třídy odregistrovat při ukončení knihovny DLL (ve vaší [DllMain](/windows/desktop/Dlls/dllmain) funkce). Pokud tak neučiníte, může způsobit `RegisterClass` k neočekávanému selhání při další klientská aplikace pokouší použít vaši knihovnu DLL.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
