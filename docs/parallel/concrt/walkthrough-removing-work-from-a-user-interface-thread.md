---
title: 'Návod: Odstranění práce z vlákna uživatelského rozhraní'
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 52bc98ef339a19c6ec2a53697f532a9a94b6c9a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377445"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Návod: Odstranění práce z vlákna uživatelského rozhraní

Tento dokument ukazuje, jak použít modul Souběžnost Runtime přesunout práci, která je prováděna podprocesem uživatelského rozhraní (UI) v aplikaci Microsoft Foundation Classes (MFC) do pracovního vlákna. Tento dokument také ukazuje, jak zlepšit výkon zdlouhavé operace kreslení.

Odebrání práce z vlákna uživatelského rozhraní převedením blokování operací, například kreslení, pracovní podprocesy může zlepšit odezvu vaší aplikace. Tento návod používá rutinu výkresu, která generuje Fraktál Mandelbrot k předvedení zdlouhavé blokovací operace. Generování Fraktála Mandelbrot je také dobrým kandidátem pro paralelizaci, protože výpočty každého pixelu jsou nezávislé na všech ostatních výpočtech.

## <a name="prerequisites"></a>Požadavky

Před zahájením tohoto návodu si přečtěte následující témata:

- [Paralelismus úkolu](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce předávání zpráv](../../parallel/concrt/message-passing-functions.md)

- [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)

- [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)

Doporučujeme také pochopit základy vývoje aplikací knihovny MFC a GDI+ před spuštěním tohoto návodu. Další informace o knihovně MFC naleznete v [tématu MFC Desktop Applications](../../mfc/mfc-desktop-applications.md). Další informace o GDI+ naleznete v tématu [GDI+](/windows/win32/gdiplus/-gdiplus-gdi-start).

## <a name="sections"></a><a name="top"></a>Oddíly

Tento návod obsahuje následující části:

- [Vytvoření aplikace knihovny MFC](#application)

- [Implementace sériové verze aplikace Mandelbrot](#serial)

- [Odebrání práce z vlákna uživatelského rozhraní](#removing-work)

- [Zlepšení výkonu výkresu](#performance)

- [Přidání podpory pro zrušení](#cancellation)

## <a name="creating-the-mfc-application"></a><a name="application"></a>Vytvoření aplikace knihovny MFC

Tato část popisuje, jak vytvořit základní aplikaci knihovny MFC.

### <a name="to-create-a-visual-c-mfc-application"></a>Vytvoření aplikace knihovny MFC visual c++

1. Pomocí **Průvodce aplikací knihovny MFC** vytvořte aplikaci knihovny MFC se všemi výchozími nastaveními. Pokyny k otevření průvodce pro vaši verzi sady Visual Studio naleznete v [tématu Návod: Pomocí nových ovládacích prvků prostředí knihovny MFC.](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md)

1. Zadejte například `Mandelbrot`název projektu a klepnutím na **tlačítko OK** zobrazte Průvodce aplikací **knihovny MFC**.

1. V podokně **Typ aplikace** vyberte **Jeden dokument**. Ujistěte se, že je zaškrtnutí políčka **Podpora architektury dokument/zobrazení** není zaškrtnuto.

1. Klepnutím na **tlačítko Dokončit** vytvořte projekt a zavřete Průvodce **aplikací knihovny MFC**.

   Ověřte, zda byla aplikace úspěšně vytvořena sestavením a spuštěním. Chcete-li vytvořit aplikaci, klikněte v nabídce **Sestavení** na **tlačítko Sestavit řešení**. Pokud se aplikace úspěšně vytvoří, spusťte aplikaci klepnutím na tlačítko **Spustit ladění v** nabídce **Ladění.**

## <a name="implementing-the-serial-version-of-the-mandelbrot-application"></a><a name="serial"></a>Implementace sériové verze aplikace Mandelbrot

Tato část popisuje, jak nakreslit fraktál Mandelbrot. Tato verze nakreslí Fraktál Mandelbrot do objektu [Bitmap](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) GDI+ a potom zkopíruje obsah této bitmapy do okna klienta.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Implementace sériové verze aplikace Mandelbrot

1. V *pch.h* (*stdafx.h* v Visual Studiu 2017 a starší) přidejte následující `#include` direktivu:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. V ChildView.h, `pragma` po směrnice, `BitmapPtr` definujte typ. Typ `BitmapPtr` umožňuje ukazatel na `Bitmap` objekt, který má být sdílen více součástmi. Objekt `Bitmap` je odstraněn, pokud již není odkazováno žádnou součástí.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. V ChildView.h přidejte do `protected` části třídy `CChildView` následující kód:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. V ChildView.cpp, komentář nebo odebrat následující řádky.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   V sestavení ladění tento krok zabrání aplikaci `DEBUG_NEW` používat alokátor, který je nekompatibilní s GDI+.

1. V ChildView.cpp přidejte direktivu `using` do `Gdiplus` oboru názvů.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Přidejte následující kód do konstruktoru a `CChildView` destruktoru třídy pro inicializaci a vypnutí GDI+.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Implementujte `CChildView::DrawMandelbrot` metodu. Tato metoda nakreslí Fraktál Mandelbrot do zadaného `Bitmap` objektu.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Implementujte `CChildView::OnPaint` metodu. Tato metoda `CChildView::DrawMandelbrot` volá a potom `Bitmap` zkopíruje obsah objektu do okna.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Ověřte, zda byla aplikace úspěšně aktualizována sestavením a spuštěním.

Následující obrázek znázorňuje výsledky aplikace Mandelbrot.

![Aplikace Mandelbrot](../../parallel/concrt/media/mandelbrot.png "Aplikace Mandelbrot")

Vzhledem k tomu, že výpočty pro každý pixel je výpočtově nákladné, vlákno uživatelského rozhraní nemůže zpracovat další zprávy, dokud nebude dokončen celkový výpočt. To může snížit odezvu v aplikaci. Tento problém však můžete zmírnit odebráním práce z vlákna uživatelského rozhraní.

[[Nahoře]](#top)

## <a name="removing-work-from-the-ui-thread"></a><a name="removing-work"></a>Odebrání práce z vlákna uživatelského rozhraní

Tato část ukazuje, jak odebrat práci výkresu z vlákna uživatelského rozhraní v aplikaci Mandelbrot. Přesunutím výkresové práce z vlákna uživatelského rozhraní do pracovního vlákna může vlákno uživatelského rozhraní zpracovat zprávy, protože pracovní vlákno generuje obrázek na pozadí.

Modul Souběžnost Runtime poskytuje tři způsoby spouštění úloh: [skupiny úloh](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)a [zjednodušené úlohy](../../parallel/concrt/task-scheduler-concurrency-runtime.md). I když můžete použít některý z těchto mechanismů odebrat práci z vlákna uživatelského rozhraní, tento příklad používá [concurrency::task_group](reference/task-group-class.md) objekt, protože skupiny úloh podporují zrušení. Tento návod později používá zrušení snížit množství práce, která se provádí při velikosti okna klienta a provést vyčištění při zničení okna.

Tento příklad také používá [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objekt povolit vlákno uživatelského rozhraní a pracovní vlákno komunikovat mezi sebou. Poté, co pracovní vlákno vytvoří obraz, odešle ukazatel na `Bitmap` objekt do objektu `unbounded_buffer` a potom odešle zprávu o malování do vlákna uživatelského rozhraní. Vlákno uživatelského rozhraní pak `unbounded_buffer` obdrží `Bitmap` z objektu objektu a nakreslí jej do okna klienta.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Odebrání výkresové práce z vlákna uživatelského rozhraní

1. V *pch.h* (*stdafx.h* v Visual Studiu 2017 a starší) přidejte následující `#include` direktivy:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. V ChildView.h `task_group` přidat `unbounded_buffer` a členské `protected` proměnné do `CChildView` části třídy. Objekt `task_group` obsahuje úkoly, které provádějí výkres; `unbounded_buffer` objekt obsahuje dokončený obraz Mandelbrot.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. V ChildView.cpp přidejte direktivu `using` do `concurrency` oboru názvů.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. V `CChildView::DrawMandelbrot` metodě po volání `Bitmap::UnlockBits`volání volání [funkce concurrency::send](reference/concurrency-namespace-functions.md#send) předat `Bitmap` objekt do vlákna uživatelského rozhraní. Potom zaúčtovat zprávu o malování do vlákna uživatelského rozhraní a zneplatnit klientské oblasti.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Aktualizujte `CChildView::OnPaint` metodu pro `Bitmap` příjem aktualizovaného objektu a nakreslete obrázek do okna klienta.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   Metoda `CChildView::OnPaint` vytvoří úkol pro generování image Mandelbrot, pokud neexistuje ve vyrovnávací paměti zprávy. Vyrovnávací paměť zprávy nebude `Bitmap` obsahovat objekt v případech, jako je například počáteční zpráva malování a při přesunutí jiného okna před okno klienta.

1. Ověřte, zda byla aplikace úspěšně aktualizována sestavením a spuštěním.

Uživatelské rozhraní je nyní citlivější, protože práce kreslení se provádí na pozadí.

[[Nahoře]](#top)

## <a name="improving-drawing-performance"></a><a name="performance"></a>Zlepšení výkonu výkresu

Generování Fraktála Mandelbrot je dobrým kandidátem pro paralelizaci, protože výpočty každého pixelu jsou nezávislé na všech ostatních výpočtech. Chcete-li paralelizovat postup kreslení, `for` převeďte vnější smyčku v metodě `CChildView::DrawMandelbrot` na volání algoritmu [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) následujícím způsobem.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Vzhledem k tomu, že výpočtkaždého bitmapového prvku je nezávislý, není třeba synchronizovat operace kreslení, které přistupují k bitmapové paměti. To umožňuje škálování výkonu s počtem dostupných procesorů.

[[Nahoře]](#top)

## <a name="adding-support-for-cancellation"></a><a name="cancellation"></a>Přidání podpory pro zrušení

Tato část popisuje, jak zpracovat velikost okna a jak zrušit všechny aktivní úkoly kreslení při zničení okna.

Zrušení dokumentu [v PPL](cancellation-in-the-ppl.md) vysvětluje, jak zrušení funguje v běhu. Zrušení je družstvo; proto k němu nedochází okamžitě. Chcete-li zastavit zrušenou úlohu, runtime vyvolá vnitřní výjimku během následného volání z úlohy do runtime. Předchozí část ukazuje, jak `parallel_for` pomocí algoritmu zlepšit výkon úkolu kreslení. Volání umožňuje `parallel_for` za běhu zastavit úlohu a proto umožňuje zrušení práce.

### <a name="cancelling-active-tasks"></a>Zrušení aktivních úkolů

Aplikace Mandelbrot `Bitmap` vytvoří objekty, jejichž rozměry odpovídají velikosti okna klienta. Pokaždé, když je velikost okna klienta, aplikace vytvoří další úlohu na pozadí pro generování bitové kopie pro novou velikost okna. Aplikace nevyžaduje tyto mezilehlé obrázky; vyžaduje pouze obrázek pro konečnou velikost okna. Chcete-li aplikaci zabránit v provádění této další práce, můžete zrušit všechny `WM_SIZE` `WM_SIZING` aktivní úlohy kreslení v obslužných rutinách zpráv pro zprávy a a poté přeplánovat práci při kreslení po změny velikosti okna.

Chcete-li zrušit aktivní úkoly kreslení při změny velikosti okna, aplikace volá [metodu concurrency::task_group::cancel](reference/task-group-class.md#cancel) v obslužných rutinách pro `WM_SIZING` zprávy a. `WM_SIZE` Obslužná rutina `WM_SIZE` zprávy také volá [metodu concurrency::task_group::wait,](reference/task-group-class.md#wait) aby počkala na dokončení všech aktivních úkolů a poté přeplánuje úlohu výkresu pro aktualizovanou velikost okna.

Při zničení okna klienta je vhodné zrušit všechny aktivní úkoly kreslení. Zrušení všech aktivních úloh kreslení zajišťuje, že pracovní vlákna nezaúčtují zprávy do vlákna uživatelského rozhraní po zničení okna klienta. Aplikace zruší všechny aktivní úkoly kreslení `WM_DESTROY` v obslužné rutině zprávy.

### <a name="responding-to-cancellation"></a>Reakce na zrušení

Metoda, `CChildView::DrawMandelbrot` která provádí úlohu kreslení, musí reagovat na zrušení. Vzhledem k tomu, že runtime `CChildView::DrawMandelbrot` používá zpracování výjimek ke zrušení úloh, musí metoda použít mechanismus bezpečný pro výjimky, který zaručí, že všechny prostředky jsou správně vyčištěny. Tento příklad používá vzor *Pořízení zdrojů je inicializace* (RAII) k zajištění, že bitmapové bitové bity jsou odemčeny při zrušení úlohy.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Přidání podpory pro zrušení v aplikaci Mandelbrot

1. V ChildView.h, `protected` v části `CChildView` třídy, přidejte `OnSize` `OnSizing`deklarace `OnDestroy` pro , a funkce mapy zpráv.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. V souboru ChildView.cpp upravte mapu zpráv `WM_SIZE` `WM_SIZING`tak, `WM_DESTROY` aby obsahovala obslužné rutiny pro soubor , a zprávy.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Implementujte `CChildView::OnSizing` metodu. Tato metoda zruší všechny existující úkoly výkresu.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Implementujte `CChildView::OnSize` metodu. Tato metoda zruší všechny existující úkoly výkresu a vytvoří novou úlohu výkresu pro aktualizovanou velikost okna klienta.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Implementujte `CChildView::OnDestroy` metodu. Tato metoda zruší všechny existující úkoly výkresu.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. V ChildView.cpp definujte třídu, `scope_guard` která implementuje vzor RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Přidejte následující kód `CChildView::DrawMandelbrot` do metody `Bitmap::LockBits`po volání :

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Tento kód zpracovává zrušení `scope_guard` vytvořením objektu. Když objekt opustí obor, odemkne bitmapové bity.

1. Upravte konec `CChildView::DrawMandelbrot` metody pro `scope_guard` zavření objektu po odemknutí bitmapových bitových bitů, ale před odesláním všech zpráv do vlákna uživatelského rozhraní. Tím zajistíte, že vlákno uživatelského rozhraní není aktualizovánpřed bitmapové bitové bity jsou odemčeny.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

1. Ověřte, zda byla aplikace úspěšně aktualizována sestavením a spuštěním.

Při změně velikosti okna se práce kreslení provádí pouze pro konečnou velikost okna. Všechny aktivní úkoly kreslení jsou také zrušeny při zničení okna.

[[Nahoře]](#top)

## <a name="see-also"></a>Viz také

[Návody runtime souběžnosti](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Paralelismus úkolu](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Desktopové aplikace knihovny MFC](../../mfc/mfc-desktop-applications.md)
