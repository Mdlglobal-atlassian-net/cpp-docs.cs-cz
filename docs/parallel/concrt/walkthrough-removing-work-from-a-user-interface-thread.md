---
title: 'Návod: Odebrání práce z vlákna uživatelského rozhraní'
ms.date: 04/25/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 214796777968c8aec7116a848e791aeef0d3af7b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512264"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Návod: Odebrání práce z vlákna uživatelského rozhraní

Tento dokument ukazuje, jak použít Concurrency Runtime k přesunutí práce prováděné vláknem uživatelského rozhraní (UI) v aplikaci Microsoft Foundation Classes (MFC) do pracovního vlákna. Tento dokument také ukazuje, jak zlepšit výkon operace vykreslování s dlouhým výkonem.

Odebrání práce z vlákna uživatelského rozhraní snižováním zátěžových operací, například kreslení, na pracovní vlákna, může zlepšit rychlost odezvy vaší aplikace. Tento návod používá vykreslovací rutinu, která generuje Mandelbrot Fractal, která demonstruje zdlouhavou operaci blokování. Generování Mandelbrot Fractal je také dobrým kandidátem na paralelismus, protože výpočet každého pixelu je nezávislý na všech ostatních výpočtech.

## <a name="prerequisites"></a>Požadavky

Než začnete tento návod, přečtěte si následující témata:

- [Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)

- [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)

- [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)

Před zahájením tohoto návodu doporučujeme také pochopit základy vývoje aplikací MFC a rozhraní GDI+. Další informace o knihovně MFC naleznete v tématu [MFC Desktop Applications](../../mfc/mfc-desktop-applications.md). Další informace o rozhraní GDI+ najdete v tématu [GDI+](/windows/win32/gdiplus/-gdiplus-gdi-start).

##  <a name="top"></a>Řezů

Tento návod obsahuje následující oddíly:

- [Vytvoření aplikace MFC](#application)

- [Implementace sériové verze aplikace Mandelbrot](#serial)

- [Odebrání práce z vlákna uživatelského rozhraní](#removing-work)

- [Zlepšení výkonu při kreslení](#performance)

- [Přidání podpory pro zrušení](#cancellation)

##  <a name="application"></a>Vytvoření aplikace MFC

Tato část popisuje, jak vytvořit základní aplikaci MFC.

### <a name="to-create-a-visual-c-mfc-application"></a>Vytvoření aplikace Visual C++ MFC

1. Použijte **Průvodce aplikací knihovny MFC** k vytvoření aplikace MFC se všemi výchozími nastaveními. Viz [Návod: Použití nových ovládacích prvků](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md) prostředí MFC pro pokyny k otevření Průvodce pro vaši verzi sady Visual Studio.

1. Zadejte název projektu, `Mandelbrot`například, a poté kliknutím na tlačítko **OK** zobrazte **Průvodce aplikací knihovny MFC**.

1. V podokně **Typ aplikace** vyberte možnost **jeden dokument**. Zajistěte, aby bylo zrušeno zaškrtnutí políčka **Podpora architektury dokument/zobrazení** .

1. Kliknutím na tlačítko **Dokončit** vytvořte projekt a zavřete **Průvodce aplikací knihovny MFC**.

   Vytvořením a spuštěním aplikace ověřte, zda byla aplikace vytvořena úspěšně. Chcete-li sestavit aplikaci, klikněte v nabídce **sestavení** na příkaz **Sestavit řešení**. Pokud se aplikace úspěšně sestaví, spusťte aplikaci kliknutím na příkaz **Spustit ladění** v nabídce **ladění** .

##  <a name="serial"></a>Implementace sériové verze aplikace Mandelbrot

Tato část popisuje, jak vykreslit Mandelbrot Fractal. Tato verze nakreslí Mandelbrot Fractal na [bitmapový](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) objekt GDI+ a pak zkopíruje obsah tohoto rastrového obrázku do okna klienta.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Implementace sériové verze aplikace Mandelbrot

1. Do souboru stdafx. h přidejte následující `#include` direktivu:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. V ChildView. h za `pragma` direktivou `BitmapPtr` Definujte typ. Typ umožňuje, aby ukazatel `Bitmap` na objekt sdílel více komponent. `BitmapPtr` Objekt `Bitmap` je odstraněn, když na něj již neodkazuje žádná součást.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. V ChildView. h přidejte následující kód do `protected` oddílu `CChildView` třídy:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. V ChildView. cpp, odkomentujte nebo odeberte následující řádky.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   V ladicích sestaveních tento krok zabrání aplikaci v použití `DEBUG_NEW` modulu přidělování, který je nekompatibilní s rozhraním GDI+.

1. V ChildView. cpp přidejte `using` do `Gdiplus` oboru názvů direktivu.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Přidejte následující kód do konstruktoru a destruktoru `CChildView` třídy pro inicializaci a vypnutí rozhraní GDI+.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Implementujte `CChildView::DrawMandelbrot` metodu. Tato metoda nakreslí Mandelbrot Fractal na zadaný `Bitmap` objekt.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Implementujte `CChildView::OnPaint` metodu. Tato metoda volá `CChildView::DrawMandelbrot` a poté zkopíruje obsah `Bitmap` objektu do okna.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Vytvořením a spuštěním aplikace ověřte, zda byla aplikace úspěšně aktualizována.

Následující ilustrace znázorňuje výsledky aplikace Mandelbrot.

![Aplikace Mandelbrot](../../parallel/concrt/media/mandelbrot.png "Aplikace Mandelbrot")

Vzhledem k tomu, že výpočet pro každý pixel je výpočetně nákladný, vlákno uživatelského rozhraní nemůže zpracovávat další zprávy, dokud se nedokončí celkový výpočet. To může zpomalit odezvu v aplikaci. Tento problém však můžete odebrat odebráním práce z vlákna uživatelského rozhraní.

[[Nahoře](#top)]

##  <a name="removing-work"></a>Odebrání práce z vlákna uživatelského rozhraní

V této části se dozvíte, jak odebrat práci s kreslením z vlákna uživatelského rozhraní v aplikaci Mandelbrot. Přesunutím práce z vlákna uživatelského rozhraní do pracovního vlákna může vlákno uživatelského rozhraní zpracovávat zprávy, když pracovní vlákno vygeneruje obrázek na pozadí.

Concurrency Runtime poskytuje tři způsoby, jak spouštět úlohy: [skupiny úloh](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)a [jednoduché úlohy](../../parallel/concrt/task-scheduler-concurrency-runtime.md). I když můžete použít kterýkoli z těchto mechanismů k odebrání práce z vlákna uživatelského rozhraní, tento příklad používá objekt [Concurrency:: task_group](reference/task-group-class.md) , protože skupiny úloh podporují zrušení. Tento návod později používá zrušení k omezení množství práce, která je provedena při změně velikosti okna klienta, a k provedení vyčištění při zničení okna.

Tento příklad také používá objekt [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) , který umožňuje VLÁKNU uživatelského rozhraní a pracovnímu vláknu vzájemně komunikovat. Poté, co pracovní vlákno vytvoří obrázek, pošle ukazatel na `Bitmap` objekt `unbounded_buffer` objektu a pak odešle zprávu o Malování do vlákna uživatelského rozhraní. Vlákno UI pak získá objekt z `unbounded_buffer` `Bitmap` objektu a nakreslí ho do okna klienta.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Odebrání práce kreslení z vlákna uživatelského rozhraní

1. Do souboru stdafx. h přidejte následující `#include` direktivy:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. V ChildView. h, přidejte `task_group` a `unbounded_buffer` členské proměnné `CChildView` do `protected` oddílu třídy. Objekt obsahuje úlohy, které provádějí vykreslování `unbounded_buffer` ; objekt obsahuje dokončenou image Mandelbrot. `task_group`

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. V ChildView. cpp přidejte `using` do `concurrency` oboru názvů direktivu.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. V metodě po `Bitmap::UnlockBits`volání volejte funkci `Bitmap` [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) pro předání objektu vláknu uživatelského rozhraní. `CChildView::DrawMandelbrot` Pak odešlete zprávu o Malování do vlákna uživatelského rozhraní a zrušte ověření klientské oblasti.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Aktualizujte `Bitmap` metodu tak, aby přijímala aktualizovaný objekt a nakreslila obrázek do okna klienta. `CChildView::OnPaint`

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   `CChildView::OnPaint` Metoda vytvoří úlohu pro vygenerování obrázku Mandelbrot, pokud některý z nich neexistuje ve vyrovnávací paměti zpráv. Vyrovnávací paměť zprávy nebude obsahovat `Bitmap` objekt v případech, jako je například počáteční zpráva Malování a při přesunu jiného okna před oknem klienta.

1. Vytvořením a spuštěním aplikace ověřte, zda byla aplikace úspěšně aktualizována.

Uživatelské rozhraní je nyní rychlejší, protože kreslení funguje na pozadí.

[[Nahoře](#top)]

##  <a name="performance"></a>Zlepšení výkonu při kreslení

Generování Mandelbrot Fractal je dobrým kandidátem na paralelismus, protože výpočet každého pixelu je nezávislý na všech ostatních výpočtech. Chcete-li paralelizovat postup kreslení, převeďte `for` vnější smyčku `CChildView::DrawMandelbrot` v metodě na volání metody [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) , následovně.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Vzhledem k tomu, že výpočet každého prvku rastrového obrázku je nezávislý, není nutné synchronizovat operace kreslení, které přistupují k paměti rastrového obrázku. To umožňuje škálování na výkon, protože se zvyšuje počet dostupných procesorů.

[[Nahoře](#top)]

##  <a name="cancellation"></a>Přidání podpory pro zrušení

Tato část popisuje, jak zpracovat změnu velikosti okna a jak zrušit všechny aktivní úlohy kreslení při zničení okna.

Zrušení dokumentu [ve PPL](cancellation-in-the-ppl.md) vysvětluje, jak zrušení funguje v modulu runtime. Zrušení je kooperativní; proto k němu nedochází hned. Chcete-li zastavit zrušený úkol, modul runtime vyvolá vnitřní výjimku při následném volání z úlohy do modulu runtime. V předchozí části se dozvíte, jak `parallel_for` použít algoritmus pro zlepšení výkonu úlohy kreslení. Volání, které `parallel_for` umožňuje modulu runtime zastavit úlohu, a proto umožňuje zrušení práce.

### <a name="cancelling-active-tasks"></a>Rušení aktivních úloh

Aplikace Mandelbrot vytvoří `Bitmap` objekty, jejichž rozměry odpovídají velikosti okna klienta. Pokaždé, když se změní velikost okna klienta, aplikace vytvoří další úlohu na pozadí, která vygeneruje obrázek pro nové velikosti okna. Aplikace nevyžaduje tyto mezilehlé image. vyžaduje pouze obrázek pro konečnou velikost okna. Chcete-li aplikaci zabránit v provádění této další práce, můžete zrušit všechny aktivní úlohy kreslení v obslužných rutinách zpráv `WM_SIZE` pro `WM_SIZING` zprávy a a pak znovu naplánovat práci při kreslení po změně velikosti okna.

Chcete-li zrušit aktivní úlohy kreslení při změně velikosti okna, aplikace zavolá metodu [Concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) v obslužných rutinách pro `WM_SIZING` zprávy a. `WM_SIZE` Obslužná rutina `WM_SIZE` zprávy také volá metodu [Concurrency:: task_group:: wait](reference/task-group-class.md#wait) , aby čekala na dokončení všech aktivních úloh, a poté znovu naplánovala úlohu kreslení pro aktualizovanou velikost okna.

Po zničení okna klienta je vhodné zrušit všechny aktivní úlohy kreslení. Zrušením aktivních úloh kreslení se zajistí, že pracovní vlákna po zničení okna klienta neodesílají zprávy do vlákna uživatelského rozhraní. Aplikace zruší všechny aktivní úlohy kreslení v obslužné rutině `WM_DESTROY` zprávy.

### <a name="responding-to-cancellation"></a>Reakce na zrušení

`CChildView::DrawMandelbrot` Metoda, která provádí úlohu kreslení, musí reagovat na zrušení. Vzhledem k tomu, že modul runtime používá zpracování výjimek ke `CChildView::DrawMandelbrot` zrušení úloh, metoda musí použít mechanismus bezpečný pro výjimku, aby bylo zaručeno, že všechny prostředky budou správně vyčištěny. V tomto příkladu se používá vzor pro *získání prostředků* (RAII), který zaručuje, že při zrušení úlohy dojde k odemčení bitů rastrového obrázku.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Přidání podpory pro zrušení v aplikaci Mandelbrot

1. V ChildView. h v `protected` části `CChildView` třídy přidejte deklarace pro `OnSize`funkce map, `OnSizing`a `OnDestroy` .

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. V ChildView. cpp Upravte mapu zprávy tak, aby obsahovala obslužné rutiny pro `WM_SIZE`zprávy `WM_DESTROY` , `WM_SIZING`a.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Implementujte `CChildView::OnSizing` metodu. Tato metoda zruší všechny existující úlohy kreslení.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Implementujte `CChildView::OnSize` metodu. Tato metoda zruší všechny existující úlohy kreslení a vytvoří novou úlohu kreslení pro aktualizovanou velikost okna klienta.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Implementujte `CChildView::OnDestroy` metodu. Tato metoda zruší všechny existující úlohy kreslení.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. V ChildView. cpp definujte `scope_guard` třídu, která implementuje vzor RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Přidejte následující kód do `CChildView::DrawMandelbrot` metody po `Bitmap::LockBits`volání:

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Tento kód zpracovává zrušení vytvořením `scope_guard` objektu. Když objekt opustí rozsah, odemkne rastrové bity.

1. Upravte konec `CChildView::DrawMandelbrot` metody pro `scope_guard` zavření objektu po odemčení rastrových bitů, ale před odesláním všech zpráv do vlákna uživatelského rozhraní. Tím se zajistí, že před odemknutím rastrových obrázků není vlákno uživatelského rozhraní aktualizováno.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. Vytvořením a spuštěním aplikace ověřte, zda byla aplikace úspěšně aktualizována.

Při změně velikosti okna se kreslení provádí pouze v konečné velikosti okna. Při zničení okna se také zruší všechny aktivní úlohy kreslení.

[[Nahoře](#top)]

## <a name="see-also"></a>Viz také:

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Desktopové aplikace knihovny MFC](../../mfc/mfc-desktop-applications.md)
