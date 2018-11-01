---
title: 'Návod: Odstranění práce z vlákna uživatelského rozhraní'
ms.date: 11/04/2016
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 85622b68f94342ece2c9fc666b9ff6d515cfe10b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472434"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Návod: Odstranění práce z vlákna uživatelského rozhraní

Tento dokument popisuje způsob použití Concurrency Runtime pro přesun práce, která se provádí pomocí vlákna uživatelského rozhraní (UI) v aplikaci Microsoft Foundation Classes (MFC) pracovní vlákno. Tento dokument také ukazuje, jak zlepšit výkon operace s delším průběhem výkresu.

Odstranění práce z vlákna uživatelského rozhraní přesměrováním blokující operace, například kreslení, pracovních vláken může zlepšit rychlost reakce aplikace. Tento návod používá výkresu rutinu, která generuje fraktálový Mandelbrot k předvedení operace s delším průběhem blokování. Generování fraktálový Mandelbrot je také vhodným kandidátem pro paralelizaci, protože je výpočet každý pixel nezávisle na jiných výpočty.

## <a name="prerequisites"></a>Požadavky

Před zahájením tohoto návodu, přečtěte si následující témata:

- [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)

- [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)

- [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)

Doporučujeme také, že chápete základy vývoje aplikací knihovny MFC a rozhraní GDI + před zahájením tohoto návodu. Další informace o rozhraní MFC naleznete v tématu [desktopových aplikací knihovny MFC](../../mfc/mfc-desktop-applications.md). Další informace o rozhraní GDI + najdete v tématu [rozhraní GDI +](https://msdn.microsoft.com/library/windows/desktop/ms533798).

##  <a name="top"></a> Oddíly

Tento návod obsahuje následující části:

- [Vytvoření aplikace MFC](#application)

- [Implementace sériového portu verze Mandelbrot aplikace](#serial)

- [Odstranění práce z vlákna uživatelského rozhraní](#removing-work)

- [Zvýšení výkonu vykreslování](#performance)

- [Přidání podpory pro zrušení](#cancellation)

##  <a name="application"></a> Vytvoření aplikace MFC

Tato část popisuje, jak vytvořit základní aplikaci knihovny MFC.

### <a name="to-create-a-visual-c-mfc-application"></a>Vytvoření aplikace v jazyce Visual C++ MFC

1. Na **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.

1. V **nový projekt** v dialogu **nainstalované šablony** vyberte **Visual C++** a pak na **šablony** vyberte **Aplikace knihovny MFC**. Zadejte název projektu, například `Mandelbrot`a potom klikněte na tlačítko **OK** zobrazíte **Průvodce aplikací knihovny MFC**.

1. V **typ aplikace** vyberte **jednotlivý dokument**. Ujistěte se, že **podpora architektury Document/View** zrušení zaškrtnutí políčka.

1. Klikněte na tlačítko **Dokončit** vytvoření projektu a zavřete **Průvodce aplikací knihovny MFC**.

   Ověřte, že aplikace úspěšně vytvořil sestavováním a spouštěním ho. Jak vytvořit aplikaci, na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Je-li aplikace sestavena úspěšně, spusťte aplikaci kliknutím **spustit ladění** na **ladění** nabídky.

##  <a name="serial"></a> Implementace sériového portu verze Mandelbrot aplikace

Tato část popisuje, jak nakreslit fraktálový Mandelbrot. Tato verze nakreslí fraktálový Mandelbrot rozhraní GDI + [rastrový obrázek](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-bitmap) objektu a pak zkopíruje obsah tento rastrový obrázek do okna klienta.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>K implementaci sériového portu verze Mandelbrot aplikace

1. Ve stdafx.h přidejte následující `#include` – direktiva:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. V ChildView.h až `pragma` směrnice, definovat `BitmapPtr` typu. `BitmapPtr` Umožňuje ukazatel na typ `Bitmap` objektu, který chcete sdílet víc součástí. `Bitmap` Odstranění objektu, když je již neodkazuje libovolné součásti.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. V ChildView.h, přidejte následující kód, který `protected` část `CChildView` třídy:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. V ChildView.cpp okomentujte nebo odstraňte následující řádky.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   V sestavení ladění, tento krok zabrání aplikaci od používání `DEBUG_NEW` alokátoru, který není kompatibilní s rozhraní GDI +.

1. V ChildView.cpp, přidejte `using` direktivu `Gdiplus` oboru názvů.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Následující kód přidejte konstruktor a destruktor `CChildView` třídy k inicializaci a ukončení rozhraní GDI +.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Implementace `CChildView::DrawMandelbrot` metody. Tato metoda vykreslí fraktálový Mandelbrot do zadaného `Bitmap` objektu.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Implementace `CChildView::OnPaint` metody. Tato metoda volá `CChildView::DrawMandelbrot` a pak zkopíruje obsah `Bitmap` objekt do okna.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

9. Ověřte, že aplikace byla úspěšně aktualizována sestavováním a spouštěním ho.

Následující obrázek znázorňuje výsledky Mandelbrot aplikace.

![Aplikace Mandelbrot](../../parallel/concrt/media/mandelbrot.png "mandelbrot")

Vzhledem k tomu, že je výpočetně náročné výpočetní funkce pro každý pixel, vlákno uživatelského rozhraní nemůže zpracovat další zprávy, až do dokončení celkové výpočtu. To může snížit rychlost odezvy aplikace. Tento problém lze však obdobná podle odstranění práce z vlákna uživatelského rozhraní.

[[Horní](#top)]

##  <a name="removing-work"></a> Odstranění práce z vlákna uživatelského rozhraní

Tato část ukazuje, jak odebrat výkresu práce z vlákna uživatelského rozhraní v aplikaci Mandelbrot. Přesunutím výkresu práce z vlákna uživatelského rozhraní k pracovní podproces můžete vlákně UI při zpracování zpráv, když pracovní podproces generuje obrázek na pozadí.

Modul Concurrency Runtime poskytuje tři způsoby, jak spouštět úlohy: [skupiny úloh](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [asynchronních agentů](../../parallel/concrt/asynchronous-agents.md), a [prostých úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md). I když používáte některou z těchto mechanismů odebrání práce z vlákna uživatelského rozhraní v tomto příkladu [concurrency::task_group](reference/task-group-class.md) objektu, protože skupiny úloh podporují zrušení. Tento návod používá zrušení později, a snížit množství práce, která je provedena při změně velikosti okna klienta a pro vyčištění při zničení okna.

Tento příklad také používá [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objektu vlákna uživatelského rozhraní a vlákna pracovního procesu pro komunikaci mezi sebou. Po pracovní vlákno vytvoří bitovou kopii, odešle ukazatel `Bitmap` objektu `unbounded_buffer` objekt a potom odešle zpráva o Malování vlákno uživatelského rozhraní. Vlákna uživatelského rozhraní se pak obdrží od `unbounded_buffer` objektu `Bitmap` objektu a kreslení do okna klienta.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Chcete-li odebrat výkresu práce z vlákna uživatelského rozhraní

1. Ve stdafx.h přidejte následující `#include` direktivy:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. V ChildView.h, přidejte `task_group` a `unbounded_buffer` členské proměnné `protected` část `CChildView` třídy. `task_group` Obsahuje úlohy, které provádějí kreslení; `unbounded_buffer` dokončené Mandelbrot image obsahuje objekt.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. V ChildView.cpp, přidejte `using` direktivu `concurrency` oboru názvů.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. V `CChildView::DrawMandelbrot` po volání metody `Bitmap::UnlockBits`, volání [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce předat `Bitmap` objektu vlákna uživatelského rozhraní. Potom publikovat zprávu malby na vlákno uživatelského rozhraní a zneplatnit klientské oblasti.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Aktualizace `CChildView::OnPaint` metoda zobrazí aktualizovaný `Bitmap` objektu a nakreslete obrázek do okna klienta.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   `CChildView::OnPaint` Metoda vytvoří úlohu k vytvoření bitové kopie Mandelbrot, pokud neexistuje ve vyrovnávací paměti zpráv. Nesmí obsahovat vyrovnávací paměti zpráv `Bitmap` objektu v případech, jako je například zpráva počáteční Malování a další okno se přesune před okno klienta.

1. Ověřte, že aplikace byla úspěšně aktualizována sestavováním a spouštěním ho.

Uživatelské rozhraní je nyní rychlejší reakce, protože kreslení práce se provádí na pozadí.

[[Horní](#top)]

##  <a name="performance"></a> Zvýšení výkonu vykreslování

Generování fraktálový Mandelbrot je vhodným kandidátem pro paralelizaci, protože je výpočet každý pixel nezávisle na jiných výpočty. Paralelní zpracování procesu vykreslování, převést vnější `for` smyčky v `CChildView::DrawMandelbrot` metoda k volání [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus, následujícím způsobem.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Protože výpočet jednotlivých prvků rastrového obrázku je nezávislé, nemají synchronizovat kreslicí operace, které přistupují k paměťově rastrového obrázku. To umožňuje škálování jako počet dostupných procesorů zvýšení výkonu.

[[Horní](#top)]

##  <a name="cancellation"></a> Přidání podpory pro zrušení

Tato část popisuje, jak zpracovat změny velikosti okna a jak zrušit všechny aktivní úlohy vykreslování při zničení okna.

Dokument [zrušení v knihovně PPL](cancellation-in-the-ppl.md) vysvětluje, jak funguje zrušení v modulu runtime. Zrušení je kooperativní; Proto se nevyskytuje okamžitě. Zastavení zrušila úlohu, modul runtime vyvolá výjimku interní při následném volání z úlohy do modulu runtime. V předchozím oddílu ukazuje způsob použití `parallel_for` algoritmus pro zvýšení výkonu vykreslování úloh. Volání `parallel_for` runtime ukončení úlohy a proto umožňuje zrušení pracovat.

### <a name="cancelling-active-tasks"></a>Zrušení aktivních úloh

Vytvoří aplikaci Mandelbrot `Bitmap` objekty, jehož rozměry odpovídají velikost okna klienta. Pokaždé, když je velikost okna klienta, aplikace vytvoří úlohu na pozadí další ke generování obrazu pro novou velikost okna. Aplikace nevyžaduje, aby tyto zprostředkující Image; poslední okno velikosti vyžaduje pouze na obrázku. Chcete-li zabránit aplikaci v provádění této další práci, můžete zrušit všechny aktivní úlohy vykreslování v obslužné rutiny zpráv pro `WM_SIZE` a `WM_SIZING` zpráv a následně přeplánovat kreslení fungují po změně velikosti okna.

Zrušení aktivních úloh vykreslování při změně velikosti okna, aplikace volá [concurrency::task_group::cancel](reference/task-group-class.md#cancel) metodu obslužné rutiny `WM_SIZING` a `WM_SIZE` zprávy. Obslužná rutina pro `WM_SIZE` zprávy také volání [Concurrency::task_group:: wait](reference/task-group-class.md#wait) metodu pro čekání na všechny aktivní úkoly k dokončení a potom přeplánuje výkresu úkol pro velikost okna aktualizované.

Při zničení okno klienta je dobrým zvykem zrušit všechny aktivní úlohy vykreslování. Ruší se všechny aktivní úlohy vykreslování zajišťuje, pracovní vlákna po zničení okno klienta nezveřejňujte zprávy na vlákně UI. Zruší všechny aktivní úlohy vykreslování v obslužné rutině aplikace `WM_DESTROY` zprávy.

### <a name="responding-to-cancellation"></a>Reakce na zrušení

`CChildView::DrawMandelbrot` Metodu, která provádí úlohy vykreslování, musí odpovědět na zrušení. Vzhledem k tomu, že modul runtime používá k zrušení úloh, zpracování výjimek `CChildView::DrawMandelbrot` metoda musí zajistit, že všechny prostředky jsou správně vyčištěné použít mechanismus bezpečnost výjimek. V tomto příkladu *získání prostředků je inicializace* vzor (RAII) k zajištění, že jsou rastrové bity odemknout při zrušení úkolu.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Přidání podpory pro zrušení v aplikaci Mandelbrot

1. V ChildView.h v `protected` část `CChildView` třídy, přidejte pro deklarace `OnSize`, `OnSizing`, a `OnDestroy` funkce mapy zpráv.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. V ChildView.cpp, upravte mapování tak, aby obsahovala obslužné rutiny pro zprávy `WM_SIZE`, `WM_SIZING`, a `WM_DESTROY` zprávy.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Implementace `CChildView::OnSizing` metody. Tato metoda zruší všechny stávající úlohy vykreslování.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Implementace `CChildView::OnSize` metody. Tato metoda zruší všechny stávající úlohy vykreslování a vytvoří nový úkol vykreslování pro velikost okna aktualizovaného klienta.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Implementace `CChildView::OnDestroy` metody. Tato metoda zruší všechny stávající úlohy vykreslování.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. V ChildView.cpp, definujte `scope_guard` třídy, která implementuje vzor RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Přidejte následující kód, který `CChildView::DrawMandelbrot` po volání metody `Bitmap::LockBits`:

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Tento kód zpracovává zrušení tak, že vytvoříte `scope_guard` objektu. Pokud objekt opustí rozsah, odemkne rastrové bity.

1. Upravit konec `CChildView::DrawMandelbrot` metoda zrušíte `scope_guard` objektu po rastrové bity jsou odemčený, ale před všechny zprávy se odesílají do vlákna uživatelského rozhraní. Tím se zajistí, že vlákno uživatelského rozhraní není aktualizován před rastrové bity jsou odemknout.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. Ověřte, že aplikace byla úspěšně aktualizována sestavováním a spouštěním ho.

Pouze pro velikost poslední okno kreslení práce se provede při změně velikosti okna. Žádné aktivní úlohy vykreslování se zruší také při zničení okna.

[[Horní](#top)]

## <a name="see-also"></a>Viz také

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Desktopové aplikace knihovny MFC](../../mfc/mfc-desktop-applications.md)
