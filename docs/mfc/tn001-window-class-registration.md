---
title: 'TN001: Registrace třídy okna'
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: 95e35ddd6f55c955bc2adb7b4db2460ae84a6dc7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513543"
---
# <a name="tn001-window-class-registration"></a>TN001: Registrace třídy okna

Tato poznámka popisuje rutiny knihovny MFC, které registrují speciální [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)ES, který vyžaduje Microsoft Windows. Projednávají se konkrétní `WNDCLASS` atributy používané v prostředích MFC a oknech.

## <a name="the-problem"></a>Problém

Atributy objektu [CWnd](../mfc/reference/cwnd-class.md) , jako je `HWND` například obslužná rutina ve Windows, jsou uloženy na dvou místech: objekt `WNDCLASS`okna a. Název `WNDCLASS` se předává obecným funkcím pro vytváření oken, jako je například [CWnd:: Create](../mfc/reference/cwnd-class.md#create) a [CFrameWnd:: Create](../mfc/reference/cframewnd-class.md#create) v parametru *lpszClassName* .

Tato `WNDCLASS` akce musí být zaregistrovaná prostřednictvím jednoho ze čtyř způsobů:

- Implicitně pomocí poskytnuté `WNDCLASS`knihovny MFC.

- Implicitně podtřídou ovládacího prvku systému Windows (nebo jiného ovládacího prvku).

- Explicitně voláním knihovny MFC [AfxRegisterWndClass –](../mfc/reference/application-information-and-management.md#afxregisterwndclass) nebo [AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass).

- Explicitně voláním rutiny Windows rutiny [registerClass](/windows/win32/api/winuser/nf-winuser-registerclassw).

## <a name="wndclass-fields"></a>WNDCLASS pole

`WNDCLASS` Struktura se skládá z různých polí popisujících třídu okna. V následující tabulce jsou uvedena pole a určují, jak se používají v aplikaci knihovny MFC:

|Pole|Popis|
|-----------|-----------------|
|*lpfnWndProc*|procedura okna musí být`AfxWndProc`|
|*cbClsExtra*|Nepoužito (mělo by být nula)|
|*cbWndExtra*|Nepoužito (mělo by být nula)|
|*hInstance*|automaticky vyplněný pomocí [AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|Ikona pro okna s rámečkem, viz níže|
|*hCursor*|kurzor pro, když se překročí okno myši, najdete níže.|
|*hbrBackground*|Barva pozadí, viz níže|
|*lpszMenuName*|Nepoužito (měl by mít hodnotu NULL)|
|*lpszClassName*|název třídy, viz níže.|

## <a name="provided-wndclasses"></a>Poskytnuté WNDCLASSes

Starší verze knihovny MFC (před verzí MFC 4,0), poskytují několik předdefinovaných tříd okna. Tyto třídy okna již nejsou ve výchozím nastavení poskytovány. Aplikace by se `AfxRegisterWndClass` měly používat s příslušnými parametry.

Pokud aplikace poskytuje prostředek se zadaným ID prostředku (například AFX_IDI_STD_FRAME), knihovna MFC bude tento prostředek používat. V opačném případě bude používat výchozí prostředek. Pro ikonu se používá ikona standardní aplikace a pro kurzor se použije standardní kurzor šipky.

Dvě ikony podporují aplikace MDI s jedním typem dokumentu: jedna ikona pro hlavní aplikaci, Druhá ikona pro Windows Documents/MDIChild ikonickým. Pro více typů dokumentů s různými ikonami je nutné zaregistrovat další `WNDCLASS`ES nebo použít funkci [CFrameWnd:: LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) .

`CFrameWnd::LoadFrame`provede registraci `WNDCLASS` pomocí ID ikony, kterou zadáte jako první parametr, a následujícími standardními atributy:

- styl třídy: CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;

- AFX_IDI_STD_FRAME ikony

- kurzor šipky

- Barva pozadí COLOR_WINDOW

Hodnoty pro barvu pozadí a kurzor pro [CMDIFrameWnd –](../mfc/reference/cmdiframewnd-class.md) nejsou použity, protože klientská oblast `CMDIFrameWnd` nástroje je zcela zahrnuta v okně **MdiClient** . Společnost Microsoft nedoporučuje podtřídovat okno **MdiClient** , takže pokud je to možné, používejte standardní barvy a typy kurzorů.

## <a name="subclassing-and-superclassing-controls"></a>Podtřídy a ovládací prvky nadřazení

Pokud jste podtřídou nebo supertřída ovládací prvek Windows (například [CButton](../mfc/reference/cbutton-class.md)), třída automaticky získá `WNDCLASS` atributy, které jsou k dispozici v implementaci Windows daného ovládacího prvku.

## <a name="the-afxregisterwndclass-function"></a>Funkce AfxRegisterWndClass –

Knihovna MFC poskytuje pomocnou funkci pro registraci třídy okna. Vzhledem k sadě atributů (styl třídy okna, kurzor, Štětec pozadí a ikona) je vygenerován syntetický název a výsledná Třída okna je zaregistrována. Například

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

Tato funkce vrací dočasný řetězec generovaného názvu třídy okna. Další informace o této funkci naleznete v tématu [AfxRegisterWndClass –](../mfc/reference/application-information-and-management.md#afxregisterwndclass).

Vrácený řetězec je dočasný ukazatel na vyrovnávací paměť statického řetězce. Je platný až do dalšího volání `AfxRegisterWndClass`. Pokud chcete tento řetězec vymezit, uložte ho do proměnné [CString](../atl-mfc-shared/using-cstring.md) , jako v tomto příkladu:

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass`vyvolá výjimku [CResourceException](../mfc/reference/cresourceexception-class.md) , pokud se nepovedlo zaregistrovat třídu okna (buď z důvodu chybných parametrů, nebo z paměti Windows).

## <a name="the-registerclass-and-afxregisterclass-functions"></a>Funkce RegisterClass a AfxRegisterClass

Pokud chcete dělat něco složitějšího, než `AfxRegisterWndClass` poskytuje, můžete zavolat rozhraní API `RegisterClass` systému Windows nebo funkci `AfxRegisterClass`MFC. [](../mfc/reference/cmdichildwnd-class.md) `Create` [](../mfc/reference/cframewnd-class.md) Funkce, CFrameWnd a CMDIChildWnd – přebírají jako první parametr název řetězce lpszClassName pro třídu Window. `CWnd` Můžete použít libovolný registrovaný název třídy okna bez ohledu na metodu, kterou jste použili k její registraci.

Je důležité použít `AfxRegisterClass` (nebo `AfxRegisterWndClass`) v knihovně DLL v systému Win32. Win32 neregistruje automaticky třídy registrované knihovnou DLL, takže při ukončení knihovny DLL je nutné explicitně zrušit registraci tříd. Pomocí `AfxRegisterClass` `RegisterClass` této služby se místo toho automaticky zpracuje. `AfxRegisterClass`udržuje seznam jedinečných tříd zaregistrovaných vaší knihovnou DLL a při ukončení knihovny DLL je automaticky zruší. Při použití `RegisterClass` v knihovně DLL je nutné zajistit, aby všechny třídy byly odregistrovány při ukončení knihovny DLL (ve funkci [DllMain](/windows/win32/Dlls/dllmain) ). Pokud se to nepovede, `RegisterClass` může dojít k neočekávané chybě, když se jiná klientská aplikace pokusí použít vaši knihovnu DLL.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
