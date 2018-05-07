---
title: 'TN017: Likvidace objektů oken | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.objects
dev_langs:
- C++
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6bba255403d31e7a1fa03febb0c760d20cdc81c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tn017-destroying-window-objects"></a>TN017: Zničení objektů oken
Tato poznámka popisuje použití [CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) metoda. Tuto metodu použijte, pokud chcete nastavit vlastní přidělení `CWnd`-odvozené objekty. Tato poznámka také vysvětluje, proč byste měli používat [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) zrušení objekt C++ Windows místo `delete` operátor.  
  
 Pokud budete postupovat podle pokynů v tomto tématu, budete mít několik čištění problémy. Tyto problémy může být důsledkem problémy, jako je, že zapomenete odstranit nebo volné paměti C++, že zapomenete uvolnit systémové prostředky, jako je `HWND`s nebo uvolnění objektů příliš mnohokrát.  
  
## <a name="the-problem"></a>Problém  
 Každý objekt systému windows (objekt třídy odvozené od `CWnd`) představuje objekt C++ a `HWND`. Objekty C++ mají při přidělování v haldě aplikace a `HWND`s v systémové prostředky přiděluje správce oken. Vzhledem k tomu, že existuje několik způsobů zničit okno objekt, musí poskytujeme sadu pravidel, které brání systému nevracení prostředků nebo paměti. Tato pravidla musí také zabránit objekty a obslužné rutiny Windows zničen více než jednou.  
  
## <a name="destroying-windows"></a>Zničení oken  
 Následují dva povolených způsoby zrušení objekt systému Windows:  
  
-   Volání metody `CWnd::DestroyWindow` nebo rozhraním API systému Windows `DestroyWindow`.  
  
-   Explicitní odstranění s `delete` operátor.  
  
 Prvním případě je nástrojem nejobvyklejší. Tento případ platí i v případě, že váš kód nevyvolá `DestroyWindow` přímo. Při zavření přímo oken s rámečkem, vygeneruje tato akce `WM_CLOSE` zprávu a výchozí odpovědi na tuto zprávu je volání `DestroyWindow.` při nadřazeného okna zničení, Windows zavolá `DestroyWindow` pro všechny její podřízené položky.  
  
 Druhý případ, použití `delete` operátor pro objekty Windows by měla být výjimečných. Následující jsou některé případů, kde je pomocí `delete` nejvhodnější.  
  
## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Automatické čištění s CWnd::PostNcDestroy  
 Pokud systém zničí okno systému Windows, je poslední Windows zprávou odeslanou v okně `WM_NCDESTROY`. Výchozí hodnota `CWnd` obslužné rutiny pro zprávy je [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy` bude detach `HWND` z C++ objektu a zavolejte funkci virtuální `PostNcDestroy`. Některé třídy přepsat tuto funkci C++ objekt odstranit.  
  
 Výchozí implementaci `CWnd::PostNcDestroy` neprovede žádnou akci, která je vhodná pro objekty oken, které jsou přiděleny na rámec zásobníku nebo vložené v jiné objekty. Toto není vhodná pro objekty oken, které jsou určeny přidělování v haldě bez všechny další objekty. Jinými slovy není vhodné pro objekty oken, které nejsou součástí jiné objekty C++.  
  
 Tyto třídy, které jsou určeny samostatně přidělování v haldě přepsat `PostNcDestroy` metodu za účelem `delete this`. Tento příkaz uvolní paměť přidružená k objektu C++. I když výchozí `CWnd` volání destruktoru `DestroyWindow` Pokud `m_hWnd` je jinou hodnotu než NULL, to není vést k nekonečné rekurzi protože popisovač bude mít hodnotu NULL a odpojit fázi čištění.  
  
> [!NOTE]
>  Systém obvykle volá `CWnd::PostNcDestroy` poté, co zpracuje Windows `WM_NCDESTROY` zprávy a `HWND` a objekt okno C++ již připojeni. Systém bude také zavolat `CWnd::PostNcDestroy` při provádění většiny [CWnd::Create](../mfc/reference/cwnd-class.md#create) volá, pokud dojde k selhání. Automatické čištění pravidla jsou popsané dále v tomto tématu.  
  
## <a name="auto-cleanup-classes"></a>Automatické čištění třídy  
 Následující třídy nejsou určená pro automatické čištění. Obvykle jsou vloženy v jiné objekty C++ nebo v zásobníku:  
  
-   Všechny standardní ovládací prvky Windows (`CStatic`, `CEdit`, `CListBox`a tak dále).  
  
-   Všechny podřízené windows odvozené přímo z `CWnd` (například vlastní ovládací prvky).  
  
-   Rozdělovače oken (`CSplitterWnd`).  
  
-   Výchozí ovládací pruhy (třídy odvozené od `CControlBar`, najdete v části [Technická poznámka 31](../mfc/tn031-control-bars.md) pro povolení automatického odstranění pro ovládací prvek panelu objekty).  
  
-   Dialogová okna (`CDialog`) určený pro modální dialogová okna na rámec zásobníku.  
  
-   Všechny standardní dialogová okna s výjimkou `CFindReplaceDialog`.  
  
-   V dialogových oknech výchozí vytvořené ClassWizard.  
  
 Následující třídy jsou navrženy pro automatické čištění. Obvykle jsou přidělovány samy o sobě v haldě:  
  
-   Okna s rámečkem hlavní (přímo nebo nepřímo odvozené z `CFrameWnd`).  
  
-   Zobrazení systému windows (přímo nebo nepřímo odvozené z `CView`).  
  
 Pokud chcete rozdělit tato pravidla, je nutné přepsat `PostNcDestroy` metoda v odvozené třídě. Automatické čištění přidat do vaší třídy, volat základní třídy a udělejte `delete this`. Chcete-li odebrat automatické čištění z vaší třídy, volejte `CWnd::PostNcDestroy` přímo místo z `PostNcDestroy` metoda vaší přímé základní třídy.  
  
 Nejběžnější použití změny automatické čištění chování je vytvoření nemodálního dialogu, který může být přidělen v haldě.  
  
## <a name="when-to-call-delete"></a>Když k odstranění volání  
 Doporučujeme vám, že zavoláte `DestroyWindow` zrušení objekt systému Windows, metoda C++ nebo na globální `DestroyWindow` rozhraní API.  
  
 Nevolejte na globální `DestroyWindow` rozhraní API se zničit okno podřízeného MDI. Používejte virtuální metody `CWnd::DestroyWindow` místo.  
  
 Pro okna v jazyku C++ objekty, které Neprovádět automatické čištění, pomocí `delete` operátor může způsobit, že paměti při pokusu o volání `DestroyWindow` v `CWnd::~CWnd` destruktor Pokud VTBL neukazuje správně odvozené třídy. K tomu dochází, protože systém nemůže najít, že odpovídající destroy – metoda k volání. Pomocí `DestroyWindow` místo `delete` zabraňuje tyto problémy. Protože to může být jemně chyba, kompilace v režimu ladění, vydá následující upozornění Pokud jsou v ohrožení.  
  
```  
Warning: calling DestroyWindow in CWnd::~CWnd  
    OnDestroy or PostNcDestroy in derived class will not be called  
```  
  
 V případě C++ Windows objekty, které provádějí automatické čištění, musí volat `DestroyWindow`. Pokud použijete `delete` operátor přímo, přidělení paměti diagnostiky MFC vás upozorní, že jste se uvolnění paměti dvakrát. Jsou dva výskyty první explicitní volání a nepřímé volání `delete this` implementace automatické čištění `PostNcDestroy`.  
  
 Po volání `DestroyWindow` na objekt automatické čištění, zůstanou objekt C++ kolem, ale `m_hWnd` bude mít hodnotu NULL. Po volání `DestroyWindow` na objekt automatické čištění objekt C++ bude pryč, vydání operátorem odstranění C++ implementace automatické čištění `PostNcDestroy`.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

