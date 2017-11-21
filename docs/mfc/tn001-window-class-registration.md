---
title: "TN001: Registrace tříd oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.registration
dev_langs: C++
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8278a1dd22a242834fd4559c580820ae6e69e21d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tn001-window-class-registration"></a>TN001: Registrace tříd oken
Tato poznámka popisuje MFC rutiny, které registrují speciální [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)es vyžaduje Microsoft Windows. Konkrétní `WNDCLASS` atributy používané MFC a Windows jsou popsané.  
  
## <a name="the-problem"></a>Problém  
 Atributy [CWnd](../mfc/reference/cwnd-class.md) objektů, jako je třeba `HWND` zpracování v systému Windows, jsou uloženy na dvou místech: objekt okno a `WNDCLASS`. Název `WNDCLASS` je předán Obecné okno Vytvoření funkce, jako [CWnd::Create](../mfc/reference/cwnd-class.md#create) a [CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create) v `lpszClassName` parametr.  
  
 To `WNDCLASS` musí být zaregistrován prostřednictvím jednoho z čtyři znamená:  
  
-   Implicitně pomocí MFC, poskytuje `WNDCLASS`.  
  
-   Implicitně pomocí vytvoření podtřídy ovládacího prvku systému Windows (nebo jiného ovládacího prvku).  
  
-   Explicitně voláním MFC [afxregisterwndclass –](../mfc/reference/application-information-and-management.md#afxregisterwndclass) nebo [afxregisterclass –](../mfc/reference/application-information-and-management.md#afxregisterclass).  
  
-   Explicitně voláním rutiny Windows [RegisterClass](http://msdn.microsoft.com/library/windows/desktop/ms633586).  
  
## <a name="wndclass-fields"></a>WNDCLASS pole  
 `WNDCLASS` Struktura se skládá z různých polí, které popisují třídy oken. Následující tabulka uvádí pole a určuje, jak se používají v aplikaci MFC:  
  
|Pole|Popis|  
|-----------|-----------------|  
|`lpfnWndProc`|okno proc, musí být`AfxWndProc`|  
|`cbClsExtra`|nepoužívá se (musí být nula.)|  
|`cbWndExtra`|nepoužívá se (musí být nula.)|  
|`hInstance`|automaticky vyplněno [afxgetinstancehandle –](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|  
|`hIcon`|Níže najdete ikona pro okna s rámečkem|  
|`hCursor`|Níže najdete kurzor pro při, myš není v okně|  
|`hbrBackground`|Barva pozadí naleznete níže|  
|`lpszMenuName`|nepoužívá se (by měl mít hodnotu NULL)|  
|`lpszClassName`|Název třídy, viz níže|  
  
## <a name="provided-wndclasses"></a>Zadaný WNDCLASSes  
 Starší verze knihovny MFC (před MFC 4.0), k dispozici několik předdefinovaných třídy oken. Ve výchozím nastavení se již nadále tyto třídy oken. Aplikace by měly používat `AfxRegisterWndClass` s příslušnými parametry.  
  
 Pokud aplikace obsahuje prostředek s ID zadaného prostředku (například AFX_IDI_STD_FRAME), použije MFC prostředku. V opačném případě se bude používat výchozí prostředek. Ikony ikona standardní aplikace se používá a pro kurzor, se používá standardní šipku kurzor.  
  
 Dvě ikony podporovat aplikace MDI s jedním dokumentem typy: jeden ikona hlavní aplikace, na ikonu pro systém windows ikony dokumentu nebo MDIChild. Pro více typů dokumentů s jinou ikony, je nutné zaregistrovat Další `WNDCLASS`es nebo použijte [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) funkce.  
  
 `CFrameWnd::LoadFrame`bude registrovat `WNDCLASS` pomocí ID ikonu zadáte jako první parametr a standardní následující atributy:  
  
-   třídy styl: CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;  
  
-   Ikona AFX_IDI_STD_FRAME  
  
-   šipka kurzoru  
  
-   Barva pozadí COLOR_WINDOW  
  
 Hodnoty pro barvu pozadí a kurzor pro [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) nepoužívají od klientské oblasti `CMDIFrameWnd` je zcela předmětem **MDICLIENT** okno. Společnost Microsoft nedoporučuje vytváření podtříd **MDICLIENT** okno proto používat standardní barvy a typy kurzoru, pokud je to možné.  
  
## <a name="subclassing-and-superclassing-controls"></a>Vytváření podtříd a ovládací prvky vytváření Supertříd  
 Pokud jste podtřídami nebo supertřídě Windows řízení (například [CButton](../mfc/reference/cbutton-class.md)) pak automaticky získá třídě `WNDCLASS` atributy, které jsou součástí Windows provádění této kontroly.  
  
## <a name="the-afxregisterwndclass-function"></a>Afxregisterwndclass – funkce  
 MFC poskytuje pomocné funkce pro registraci třídy oken. Danou sadu atributů (styl třídy oken, kurzoru, štětec pozadí plochy a ikonu), je generován syntetické název a výsledný okno třída je registrována. Například  
  
```  
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```  
  
 Tato funkce vrátí řetězec dočasný název třídy generované registrované okno. Další informace o této funkci najdete v tématu [afxregisterwndclass –](../mfc/reference/application-information-and-management.md#afxregisterwndclass).  
  
 Vrácený řetězec je dočasný ukazatel na statický řetězec. Je platný do další volání `AfxRegisterWndClass`. Pokud chcete, aby tento řetězec kolem, uložit jej do [CString](../atl-mfc-shared/using-cstring.md) proměnné, jako v následujícím příkladu:  
  
```  
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...  
CWnd* pWnd = new CWnd;  
pWnd->Create(strWndClass, ...);

...  
```  
  
 `AfxRegisterWndClass`vyvolá výjimku [CResourceException](../mfc/reference/cresourceexception-class.md) Pokud třída okno se nepodařilo zaregistrovat (buď z důvodu nesprávných parametrů, nebo nedostatek paměti systému Windows).  
  
## <a name="the-registerclass-and-afxregisterclass-functions"></a>RegisterClass a afxregisterclass – funkce  
 Pokud chcete udělat nic více pokročilé než co `AfxRegisterWndClass` poskytuje, můžete volat rozhraní API systému Windows `RegisterClass` nebo funkce MFC `AfxRegisterClass`. `CWnd`, [CFrameWnd](../mfc/reference/cframewnd-class.md) a [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create` funkce přebírat `lpszClassName` název řetězce pro třídu okna jako první parametr. Můžete použít jakýkoli název třídy registrované okno, bez ohledu na metodu, kterou jste použili k registraci.  
  
 Je důležité použít `AfxRegisterClass` (nebo `AfxRegisterWndClass`) v knihovně DLL na Win32. Win32 není automaticky registraci třídy registrovaných knihovny DLL, takže musí explicitně zrušení registrace třídy při ukončení knihovnu DLL. Pomocí `AfxRegisterClass` místo `RegisterClass` to zpracovává automaticky za vás. `AfxRegisterClass`udržuje seznam jedinečných tříd zaregistrovat vaše knihovna DLL a bude automaticky zrušit jejich při ukončí knihovnu DLL. Při použití `RegisterClass` v knihovně DLL, ujistěte se, zda jsou všechny třídy registrace při ukončení knihovny DLL (ve vaší [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583) funkce). Může způsobit selhání Uděláte to tak `RegisterClass` neočekávané selhání, když pokusí použít vaše knihovna DLL jinou aplikaci klienta.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

