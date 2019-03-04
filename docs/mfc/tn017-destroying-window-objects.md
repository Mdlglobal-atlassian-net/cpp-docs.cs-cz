---
title: 'TN017: Likvidace objektů oken'
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 9e52112bed0f583a3f5652f9213bd5049d543a80
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294107"
---
# <a name="tn017-destroying-window-objects"></a>TN017: Likvidace objektů oken

Tato poznámka popisuje použití [CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) metody. Tuto metodu použijte, pokud chcete provést vlastní přidělení `CWnd`-odvozené objekty. Tato poznámka také vysvětluje, proč byste měli používat [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) ke zničení objektu jazyka C++ Windows namísto **odstranit** operátor.

Pokud budete postupovat podle pokynů v tomto tématu, budete mít několik problémů vyčištění. Tyto problémy můžou být výsledkem problémy, jako je zapomínání odstranění nebo uvolnění paměti C++, zapomínání uvolnit systémové prostředky, jako je `HWND`s nebo uvolnění objektů příliš mnohokrát.

## <a name="the-problem"></a>Problém

Každý objekt windows (objekt třídy odvozené z `CWnd`) představuje objekt jazyka C++ a `HWND`. Objekty C++ jsou přiděleny do haldy vaší aplikace a `HWND`v systémové prostředky s přidělují Správce oken. Musí, protože existuje několik způsobů, jak zničit objekt window, poskytujeme sadu pravidel, která zabraňuje systému nevracení prostředku nebo paměti. Tato pravidla musí také zabránit objektů a popisovače Windows likviduje více než jednou.

## <a name="destroying-windows"></a>Zničení oken s Windows

Následují dva způsoby povolených zničit objekt Windows:

- Volání `CWnd::DestroyWindow` nebo rozhraní API Windows `DestroyWindow`.

- Explicitní odstranění se **odstranit** operátor.

Prvním případě se zdaleka nejčastěji. Tento případ platí i v případě, že váš kód nevolá `DestroyWindow` přímo. Pokud uživatel přímo zavře okno rámce, tato akce vytvoří zprávu WM_CLOSE výchozí odpověď na tuto zprávu se volat `DestroyWindow.` při zničení nadřazené okno Windows volá `DestroyWindow` pro všechny jeho podřízené objekty.

Druhý případ, použití **odstranit** by měl mít operátor pro objekty Windows výjimečný. Následující jsou některé případy, kdy použití **odstranit** je tou správnou volbou.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Automatické čištění s CWnd::PostNcDestroy

Když systém odstraní okno Windows, je poslední Windows zpráva odeslaná do okna WM_NCDESTROY. Výchozí hodnota `CWnd` obslužné rutiny pro zprávy je [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy` se odpojit `HWND` z jazyka C++ a následně zavolat virtuální funkci `PostNcDestroy`. Některé třídy přepsat tato funkce se odstranit objekt jazyka C++.

Výchozí implementace `CWnd::PostNcDestroy` neprovede žádnou akci, která je vhodná pro objekty oken, které jsou přiděleny v zásobníku nebo vložené v jiných objektech. To není vhodná pro objekty oken, které jsou navržené tak, která bude přidělena v haldě bez dalších objektů. Jinými slovy není vhodné pro objekty oken, které nejsou součástí jiných objektů jazyka C++.

Tyto třídy, které mají být samostatně přidělený k haldě přepsat `PostNcDestroy` metodu za účelem **odstranit tento**. Tento příkaz uvolní paměť přidružený objekt jazyka C++. I když výchozí `CWnd` volání destruktoru `DestroyWindow` Pokud *m_hWnd* je není NULL, to není vést k nekonečné rekurzi popisovač proto bude odpojená a NULL ve fázi čištění.

> [!NOTE]
>  Systém volá obvykle `CWnd::PostNcDestroy` po zpracování zprávy Windows WM_NCDESTROY a `HWND` a okno objekt jazyka C++ jsou již propojeny. Systém také bude volat `CWnd::PostNcDestroy` při provádění většiny [CWnd::Create](../mfc/reference/cwnd-class.md#create) zavolá, pokud dojde k chybě. Automatické čištění pravidel jsou popsány dále v tomto tématu.

## <a name="auto-cleanup-classes"></a>Automatické čištění třídy

Následující třídy nejsou určeny pro automatické čištění. Obvykle jsou vloženy do jiných objektů jazyka C++ nebo v zásobníku:

- Všechny standardní ovládací prvky Windows (`CStatic`, `CEdit`, `CListBox`, a tak dále).

- Žádné podřízená okna odvozena přímo z `CWnd` (například vlastní ovládací prvky).

- Rozdělovače oken (`CSplitterWnd`).

- Výchozí ovládací pruhy (třídy odvozené z `CControlBar`, naleznete v tématu [Technická poznámka 31](../mfc/tn031-control-bars.md) pro povolení automatické odstranění pro ovládací prvek panelu objekty).

- Dialogová okna (`CDialog`) navržené pro modální dialogová okna v rámci zásobníku.

- Všechny standardní dialogová okna s výjimkou `CFindReplaceDialog`.

- Dialogová okna výchozí vytvořené nástrojem ClassWizard.

Následující třídy jsou navržené pro automatické čištění. Obvykle jsou přidělovány samy na haldě:

- Hlavního okna s rámečkem (odvozený přímo nebo nepřímo z `CFrameWnd`).

- Zobrazení systému windows (odvozený přímo nebo nepřímo z `CView`).

Pokud chcete provést přerušení tato pravidla, je nutné přepsat `PostNcDestroy` metoda v odvozené třídě. Automatické čištění přidat do vaší třídy, volat základní třídy a proveďte **odstranit tento**. Chcete-li odebrat automatické vyčištění z vaší třídy, zavolejte `CWnd::PostNcDestroy` přímo namísto tohoto `PostNcDestroy` metoda přímou základní třídu.

Změna chování automatického čištění nejběžnější použití je vytvoření nemodálního dialogového okna, který může být přidělen na haldě.

## <a name="when-to-call-delete"></a>Pokud k volání delete

Doporučujeme vám, že zavoláte `DestroyWindow` zničit objekt Windows, metoda jazyka C++ nebo globální `DestroyWindow` rozhraní API.

Nevolejte globální `DestroyWindow` API zrušení podřízené okno MDI. By měl používal virtuální metodu `CWnd::DestroyWindow` místo.

Pro okna v jazyku C++ objekty, které neprováděl automatické čištění, pomocí **odstranit** operátor může způsobit nevracení paměti, při pokusu o volání `DestroyWindow` v `CWnd::~CWnd` destruktor, pokud VTBL neodkazuje správně odvozené třídy. K tomu dojde, protože systém nemůže najít že odpovídající metodu chce volat zničit. Pomocí `DestroyWindow` místo **odstranit** tyto problémy se vyhnete. Protože to může být drobné chyby, kompilace v režimu ladění vygeneruje toto upozornění Pokud vám hrozí.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

V případě Windows C++ objekty, které provádějí automatické čištění, je nutné volat `DestroyWindow`. Pokud používáte **odstranit** operátor přímo, přidělení paměti diagnostických MFC vás upozorní, že jste se uvolňování paměti dvakrát. Jsou dva výskyty první explicitní volání a nepřímé volání **odstranit tento** při provádění automatické čištění `PostNcDestroy`.

Po volání `DestroyWindow` na automatické vyčištění objektu, objekt jazyka C++ bude i nadále, ale *m_hWnd* budou mít hodnotu NULL. Po volání `DestroyWindow` na automatické vyčištění objektu, objekt jazyka C++ zmizí, uvolnění operátor delete C++ při provádění automatické čištění `PostNcDestroy`.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
