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
ms.openlocfilehash: 9802669468cbbba89f23b8ac127358d1fc15ec9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370426"
---
# <a name="tn017-destroying-window-objects"></a>TN017: Likvidace objektů oken

Tato poznámka popisuje použití [Metody CWnd::PostNcDestroy.](../mfc/reference/cwnd-class.md#postncdestroy) Tuto metodu použijte, pokud chcete `CWnd`provést vlastní přidělení odvozených objektů. Tato poznámka také vysvětluje, proč byste měli použít [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) zničit c++ Windows objekt namísto **delete** operátor.

Pokud budete postupovat podle pokynů v tomto tématu, budete mít několik problémů s vyčištěním. Tyto problémy mohou vyplývat z problémů, jako je například zapomínání na `HWND`odstranění/volné paměti C++, zapomínání na volné systémové prostředky, jako je s, nebo uvolnění objektů příliš mnohokrát.

## <a name="the-problem"></a>Problém

Každý objekt windows (objekt třídy `CWnd`odvozené z ) představuje `HWND`objekt Jazyka C++ i objekt . C++ objekty jsou přiděleny v haldě aplikace a `HWND`s jsou přiděleny v systémových prostředcích správce oken. Protože existuje několik způsobů, jak zničit objekt okna, musíme poskytnout sadu pravidel, která brání nevracení systémových prostředků nebo paměti. Tato pravidla musí také zabránit objekty a popisovače systému Windows z zničené více než jednou.

## <a name="destroying-windows"></a>Zničení oken

Následují dva povolené způsoby zničení objektu systému Windows:

- Volání `CWnd::DestroyWindow` nebo rozhraní `DestroyWindow`API systému Windows .

- Explicitně se odstraní s operátorem **delete.**

První případ je zdaleka nejčastější. Tento případ platí i v případě, že váš kód nevolá `DestroyWindow` přímo. Když uživatel přímo zavře okno rámce, tato akce vygeneruje zprávu WM_CLOSE a výchozí `DestroyWindow.` odpověď na tuto zprávu `DestroyWindow` je volání Při zničení nadřazeného okna systém Windows volá všechny své podřízené položky.

Druhý případ, použití operátoru **delete** na objekty systému Windows, by měla být vzácné. Následují některé případy, kdy použití **delete** je správná volba.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Automatické vyčištění s CWnd::PostNcDestroy

Když systém zničí okno systému Windows, poslední zpráva systému Windows odeslaná do okna je WM_NCDESTROY. Výchozí `CWnd` obslužná rutina pro tuto zprávu je [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy`odpojí `HWND` od objektu C++ a zavolá `PostNcDestroy`virtuální funkci . Některé třídy přepsat tuto funkci odstranit c++ objekt.

Výchozí implementace `CWnd::PostNcDestroy` neprovede žádné, což je vhodné pro objekty okna, které jsou přiděleny v rámci zásobníku nebo vložené do jiných objektů. To není vhodné pro objekty okna, které jsou určeny k přidělení na haldě bez jiných objektů. Jinými slovy není vhodné pro objekty okna, které nejsou vloženy do jiných objektů jazyka C++.

Tyto třídy, které jsou určeny k přidělení `PostNcDestroy` samostatně na haldě přepsat metodu provést **odstranit .** Tento příkaz uvolní všechny paměti spojené s objektem C++. I když `CWnd` výchozí destruktor volá, `DestroyWindow` pokud *m_hWnd* není null, to nevede k nekonečné rekurzi, protože popisovač bude odpojen a null během fáze čištění.

> [!NOTE]
> Systém obvykle `CWnd::PostNcDestroy` volá poté, co zpracovává `HWND` zprávu WM_NCDESTROY systému Windows a objekt okna C++ již nejsou připojeny. Systém bude také `CWnd::PostNcDestroy` volat v implementaci většiny [CWnd::Create](../mfc/reference/cwnd-class.md#create) volání, pokud dojde k selhání. Pravidla automatického čištění jsou popsána dále v tomto tématu.

## <a name="auto-cleanup-classes"></a>Automatické čištění třídy

Následující třídy nejsou určeny pro automatické čištění. Obvykle jsou vloženy do jiných objektů jazyka C++ nebo v zásobníku:

- Všechny standardní ovládací`CStatic` `CEdit`prvky systému Windows ( , `CListBox`, a tak dále).

- Všechna podřízená okna `CWnd` odvozená přímo z (například vlastní ovládací prvky).

- Rozbočovač`CSplitterWnd`oken ( ).

- Výchozí ovládací panely (třídy odvozené z `CControlBar`, viz [Technická poznámka 31](../mfc/tn031-control-bars.md) pro povolení automatického odstraňování objektů ovládacího panelu).

- Dialogy`CDialog`( ) určené pro modální dialogy na rámečku zásobníku.

- Všechna standardní dialogová `CFindReplaceDialog`okna s výjimkou .

- Výchozí dialogová okna vytvořená průvodcem classwizard.

Následující třídy jsou určeny pro automatické čištění. Obvykle jsou přidělovány samy o sobě na haldě:

- Okna hlavního rámu (odvozená `CFrameWnd`přímo nebo nepřímo z).

- Zobrazit okna (odvozené přímo `CView`nebo nepřímo z).

Pokud chcete porušit tato pravidla, je `PostNcDestroy` nutné přepsat metodu v odvozené třídě. Chcete-li do třídy přidat automatické vyčištění, zavolejte základní třídu a pak **odstraňte tuto třídu**. Chcete-li odebrat automatické vyčištění `CWnd::PostNcDestroy` z vaší `PostNcDestroy` třídy, volání přímo namísto metody přímé základní třídy.

Nejběžnější použití změny chování automatického čištění je vytvořit nemodální dialogové okno, které mohou být přiděleny na haldě.

## <a name="when-to-call-delete"></a>Kdy volat odstranit

Doporučujeme volat `DestroyWindow` zničit objekt systému Windows, buď c++ `DestroyWindow` metoda nebo globální rozhraní API.

Nevolejte globální `DestroyWindow` rozhraní API zničit okno Podřízené MDI. Místo toho byste `CWnd::DestroyWindow` měli použít virtuální metodu.

Pro objekty C++ Window, které neprovádějí automatické vyčištění, pomocí operátoru **odstranění** `DestroyWindow` může `CWnd::~CWnd` způsobit nevracení paměti při pokusu o volání v destruktoru, pokud VTBL neukazuje na správně odvozené třídy. K tomu dochází, protože systém nemůže najít příslušnou metodu zničení pro volání. Použití `DestroyWindow` namísto **odstranění** se těmto problémům vyhne. Vzhledem k tomu, že to může být jemná chyba, kompilace v režimu ladění vygeneruje následující upozornění, pokud jste ohroženi.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

V případě objektů systému Windows jazyka C++, které `DestroyWindow`provádějí automatické čištění, je nutné volat . Pokud použijete operátor **odstranění** přímo, alokátor diagnostické paměti knihovny MFC vás upozorní, že paměť uvolňujete dvakrát. Tyto dva výskyty jsou vaše první explicitní volání a nepřímé volání odstranit `PostNcDestroy` **v** implementaci automatickévyčištění aplikace .

Po `DestroyWindow` volání na non-auto-cleanup objektu C++ objekt bude stále kolem, ale *m_hWnd* bude null. Po `DestroyWindow` volání na objekt automatické vyčištění, bude objekt Jazyka C++pryč, uvolněna c++ odstranit operátor `PostNcDestroy`v implementaci automatického vyčištění .

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
