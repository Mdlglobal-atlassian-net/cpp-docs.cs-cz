---
title: "Návod: Odstranění práce z vlákna uživatelského rozhraní | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0372e407927d270fe5115fd3b5646d59049d269d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Návod: Odstranění práce z vlákna uživatelského rozhraní
Tento dokument ukazuje, jak pokud chcete přesunout pracovní, které se provádí pomocí uživatelského rozhraní (UI) vlákno v aplikaci Microsoft Foundation třídy (MFC) pracovní vlákno pomocí Concurrency Runtime. Tento dokument také ukazuje, jak zlepšit výkon časově náročná operace kreslení.  
  
 Odstranění práce z vlákna uživatelského rozhraní přenesením blokování operací, například kreslení na pracovních vláken může zvýšit rychlost reakce aplikace. Tento návod používá vykreslování rutiny, která generuje fraktálový Mandelbrot k předvedení časově náročná operace blokování. Generování fraktálový Mandelbrot je také vhodným kandidátem na paralelizace, protože výpočet každý pixelů je nezávislý na jiné výpočty.  
  
## <a name="prerequisites"></a>Požadavky  
 Před spuštěním tohoto průvodce, přečtěte si následující témata:  
  
-   [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Funkce usnadnění](../../parallel/concrt/message-passing-functions.md)  
  
-   [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)  
  
-   [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)  
  
 Doporučujeme taky, že chápete základní informace o vývoji aplikací MFC a [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] před spuštěním tohoto průvodce. Další informace o rozhraní MFC najdete v tématu [aplikace MFC plochy](../../mfc/mfc-desktop-applications.md). Další informace o [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)], najdete v části [GDI +](https://msdn.microsoft.com/en-us/library/windows/desktop/ms533798).  
  
##  <a name="top"></a>Oddíly  
 Tento názorný postup obsahuje následující části:  
  
-   [Vytváření aplikací MFC](#application)  
  
-   [Implementace sériové verze Mandelbrot aplikace](#serial)  
  
-   [Odstranění práce z vlákna uživatelského rozhraní](#removing-work)  
  
-   [Zlepšení výkonu kreslení](#performance)  
  
-   [Přidání podpory pro zrušení](#cancellation)  
  
##  <a name="application"></a>Vytváření aplikací MFC  
 Tato část popisuje, jak vytvořit základní aplikaci MFC.  
  
### <a name="to-create-a-visual-c-mfc-application"></a>Vytvoření aplikace Visual C++ MFC  
  
1.  Na **soubor** nabídky, klikněte na tlačítko **nový**a potom klikněte na **projektu**.  
  
2.  V **nový projekt** v dialogovém **nainstalovaných šablonách** podokně, vyberte **Visual C++**a pak na **šablony** vyberte možnost **Aplikace knihovny MFC**. Zadejte název projektu, například `Mandelbrot`a potom klikněte na **OK** zobrazíte **Průvodce aplikací knihovny MFC**.  
  
3.  V **typ aplikace** podokně, vyberte **jednotlivý dokument**. Ujistěte se, že **Document/View – architektura podporu** zaškrtnutí políčka.  
  
4.  Klikněte na tlačítko **Dokončit** vytvořte projekt a zavřete **Průvodce aplikací knihovny MFC**.  
  
     Ověřte, že aplikace byl úspěšně vytvořen vytváření a jeho spuštěním. Vytvořit aplikaci, na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Pokud aplikace sestavení úspěšně, spusťte aplikaci kliknutím **spustit ladění** na **ladění** nabídky.  
  
##  <a name="serial"></a>Implementace sériové verze Mandelbrot aplikace  
 Tato část popisuje, jak k vykreslení fraktálový Mandelbrot. Tato verze nevykresluje fraktálový Mandelbrot k [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] [rastrový obrázek](https://msdn.microsoft.com/library/ms534420.aspx) objektu a pak zkopíruje obsah bitovou mapu do okna klienta.  
  
#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>K implementaci sériové verze Mandelbrot aplikace  
  
1.  V stdafx.h, přidejte následující `#include` – direktiva:  
  
     [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]  
  
2.  V ChildView.h po `pragma` – direktiva, zadejte `BitmapPtr` typu. `BitmapPtr` Typ umožňuje ukazatel na `Bitmap` objekt, který má být sdílen více součástí. `Bitmap` Je odstraněn objekt, když už je odkazován objektem libovolné součásti.  
  
     [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]  
  
3.  V ChildView.h, přidejte následující kód, který `protected` části `CChildView` – třída:  
  
     [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]  
  
4.  V ChildView.cpp komentář nebo odeberte následující řádky.  
  
     [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]  
  
     V sestavení pro ladění, tento krok brání aplikaci v pomocí `DEBUG_NEW` allocator, který není kompatibilní s [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)].  
  
5.  V ChildView.cpp, přidejte `using` direktivy k `Gdiplus` oboru názvů.  
  
     [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]  
  
6.  Přidejte následující kód do konstruktoru a destruktoru objektu `CChildView` třídy pro inicializaci a vypnutí [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)].  
  
     [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]  
  
7.  Implementace `CChildView::DrawMandelbrot` metoda. Tato metoda vykreslí fraktálový Mandelbrot do zadané `Bitmap` objektu.  
  
     [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]  
  
8.  Implementace `CChildView::OnPaint` metoda. Tato metoda volá `CChildView::DrawMandelbrot` a pak zkopíruje obsah `Bitmap` objektu do okna.  
  
     [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]  
  
9. Ověřte, že aplikace byl úspěšně aktualizován vytváření a jeho spuštěním.  
  
 Následující obrázek znázorňuje výsledky Mandelbrot aplikace.  
  
 ![Aplikace Mandelbrot](../../parallel/concrt/media/mandelbrot.png "mandelbrot")  
  
 Protože je náročné výpočet pro každý pixelů, vlákna uživatelského rozhraní nemůže zpracovat další zprávy, dokud nebude dokončeno celkové výpočet. To může snížit odezvy v aplikaci. Můžete však zbavit tento problém tím odstranění práce z vlákna uživatelského rozhraní.  
  
 [[Horní](#top)]  
  
##  <a name="removing-work"></a>Odstranění práce z vlákna uživatelského rozhraní  
 V této části ukazuje, jak odebrat kreslení práce z vlákna uživatelského rozhraní v aplikaci Mandelbrot. Přesunutím kreslení práce z vlákna uživatelského rozhraní pro pracovní vlákno můžete vlákna uživatelského rozhraní zpracování zpráv, když pracovní vlákno generuje obrázek na pozadí.  
  
 Concurrency Runtime poskytuje tři způsoby, jak spouštět úlohy: [úkolů skupiny](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [asynchronních agentů](../../parallel/concrt/asynchronous-agents.md), a [prosté úlohy](../../parallel/concrt/task-scheduler-concurrency-runtime.md). I když používáte jednu z těchto mechanismů odebrání práce z vlákna uživatelského rozhraní v tomto příkladu [concurrency::task_group](reference/task-group-class.md) objekt, protože podporují zrušení skupiny úloh. Tento návod používá zrušení později, snížit množství práce, které se provádí při změně velikosti okna klienta a provést čištění, když okno zničena.  
  
 Tento příklad také používá [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objekt, který chcete povolit vlákna uživatelského rozhraní a pracovní vlákno pro komunikaci mezi sebou. Po pracovní vlákno vytvoří bitovou kopii, odešle ukazatel `Bitmap` do objektu `unbounded_buffer` objektu a poté odešle zprávu Malování vlákna uživatelského rozhraní. Vlákna uživatelského rozhraní, které pak obdrží od `unbounded_buffer` objektu `Bitmap` objektu a nevykresluje do okna klienta.  
  
#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Chcete-li odebrat kreslení práce z vlákna uživatelského rozhraní  
  
1.  V stdafx.h, přidejte následující `#include` direktivy:  
  
     [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]  
  
2.  V ChildView.h, přidejte `task_group` a `unbounded_buffer` členské proměnné `protected` části `CChildView` třídy. `task_group` Jaké úlohy provádějí kreslení; má objekt `unbounded_buffer` objektu obsahuje bitovou kopii Mandelbrot dokončené.  
  
     [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]  
  
3.  V ChildView.cpp, přidejte `using` direktivy k `concurrency` oboru názvů.  
  
     [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]  
  

4.  V `CChildView::DrawMandelbrot` po zavolání metody `Bitmap::UnlockBits`, volání [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce předávání `Bitmap` objekt, který má vlákna uživatelského rozhraní. Potom vystavit zprávu Malování vlákna uživatelského rozhraní a zrušit platnost klientské oblasti.  

  
     [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]  
  
5.  Aktualizace `CChildView::OnPaint` metodu aktualizovaný `Bitmap` objektu a kreslení bitovou kopii do okna klienta.  
  
     [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]  
  
     `CChildView::OnPaint` Metoda vytvoří úlohu k vytvoření bitové kopie Mandelbrot, pokud žádný neexistuje ve vyrovnávací paměti zpráv. Vyrovnávací paměť zprávu nebude obsahovat `Bitmap` objektu v případech, jako je například zpráva počáteční Malování a další okno se přesune před okna klienta.  
  
6.  Ověřte, že aplikace byl úspěšně aktualizován vytváření a jeho spuštěním.  
  
 Uživatelské rozhraní je nyní rychlejší reakce, protože kreslení pracovní probíhá na pozadí.  
  
 [[Horní](#top)]  
  
##  <a name="performance"></a>Zlepšení výkonu kreslení  

 Generování fraktálový Mandelbrot je vhodným kandidátem na paralelizace, protože výpočet každý pixelů je nezávislý na jiné výpočty. Učinit paralelní kreslení postup, převést vnější `for` smyčky v `CChildView::DrawMandelbrot` metoda k volání [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus následujícím způsobem.  

  
 [!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]  
  
 Protože výpočet jednotlivých prvků rastrového obrázku je nezávislé, nemáte synchronizace kreslení operací, které přistupují k paměťově rastrového obrázku. To umožňuje škálovat počet dostupných procesorů zvyšuje výkon.  
  
 [[Horní](#top)]  
  
##  <a name="cancellation"></a>Přidání podpory pro zrušení  
 Tato část popisuje, jak zpracovat změny velikosti okna a jak zrušit všechny aktivní kreslení úkoly při zničena okna.  
  
 Dokument [zrušení v knihovně PPL](cancellation-in-the-ppl.md) vysvětluje, jak funguje zrušení v modulu runtime. Zrušení je spolupráci; proto ho neproběhne okamžitě. Pokud chcete zastavit úlohu zrušené, modul runtime vyvolá vnitřní výjimkou během následných volání z úlohy do modulu runtime. V předchozí části ukazuje, jak používat `parallel_for` algoritmus ke zlepšení výkonu kreslení úlohy. Volání `parallel_for` umožňuje modulu runtime ukončení úlohy a proto umožňuje zrušení pracovat.  
  
### <a name="cancelling-active-tasks"></a>Zrušení aktivních úloh  
 Vytvoří aplikace Mandelbrot `Bitmap` objekty, jejichž dimenze přizpůsobit velikost okna klienta. Pokaždé, když změníte velikost okna klienta, aplikace vytvoří úkol aplikace Další pozadí ke generování obrazu pro novou velikost okna. Aplikace nevyžaduje, aby tyto zprostředkující Image; vyžaduje pouze bitovou kopii pro velikost poslední okno. Chcete-li zabránit aplikaci v provádění této další zátěže, můžete zrušit všechny aktivní úlohy kreslení v obslužné rutiny zpráv pro `WM_SIZE` a `WM_SIZING` zprávy a následně přeplánovat kreslení fungovat po změně velikosti okna.  
  
 Zrušení aktivních úloh kreslení při změně velikosti okna, aplikace volá [concurrency::task_group::cancel](reference/task-group-class.md#cancel) metoda v obslužné rutiny `WM_SIZING` a `WM_SIZE` zprávy. Obslužná rutina pro `WM_SIZE` zpráva taky volání [concurrency::task_group::wait](reference/task-group-class.md#wait) metoda čekat všechny aktivní úlohy k dokončení a potom přeplánuje kreslení úloha pro velikost okna aktualizované.  
  
 Po zničení okna klienta, je dobrým zvykem zrušení všech aktivních úloh kreslení. Zrušení všech aktivních úloh kreslení zajišťuje, že pracovních vláken není odeslání zprávy do vlákna uživatelského rozhraní po okna klienta zničena. Zruší všechny aktivní úlohy kreslení v obslužnou rutinu pro aplikaci `WM_DESTROY` zprávy.  
  
### <a name="responding-to-cancellation"></a>Neodpovídá na požadavky zrušení  
 `CChildView::DrawMandelbrot` Metodu, která provede úlohu vykreslování, reagovat na zrušení. Vzhledem k tomu, že modul runtime používá zpracování výjimek pro zrušení úloh, `CChildView::DrawMandelbrot` metoda musí používat mechanismus výjimek bezpečných zaručit, že všechny prostředky jsou správně vyčištěné. Tento příklad používá *prostředků pořízení je inicializace* (RAII) vzor zaručit, že bits rastrového obrázku jsou odemčený, když se zruší úlohu.  
  
##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Chcete-li přidat podporu pro zrušení Mandelbrot aplikace  
  
1.  V ChildView.h v `protected` části `CChildView` třídy, přidejte deklarace pro `OnSize`, `OnSizing`, a `OnDestroy` zprávy funkce mapy.  
  
     [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]  
  
2.  V ChildView.cpp, upravte mapy zpráv tak, aby obsahovala obslužné rutiny pro `WM_SIZE`, `WM_SIZING`, a `WM_DESTROY` zprávy.  
  
     [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]  
  
3.  Implementace `CChildView::OnSizing` metoda. Tato metoda zruší všechny stávající kreslení úlohy.  
  
     [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]  
  
4.  Implementace `CChildView::OnSize` metoda. Tato metoda zruší všechny stávající kreslení úlohy a vytvoří novou úlohu vykreslování pro velikost okna aktualizovaného klienta.  
  
     [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]  
  
5.  Implementace `CChildView::OnDestroy` metoda. Tato metoda zruší všechny stávající kreslení úlohy.  
  
     [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]  
  
6.  V ChildView.cpp, zadejte `scope_guard` třídy, která implementuje vzor RAII.  
  
     [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]  
  
7.  Přidejte následující kód, který `CChildView::DrawMandelbrot` metoda po volání `Bitmap::LockBits`:  
  
     [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]  
  
     Tento kód zpracovává zrušení tak, že vytvoříte `scope_guard` objektu. Pokud objekt opustí rozsah, odemkne bits rastrového obrázku.  
  
8.  Upravit konec `CChildView::DrawMandelbrot` metoda pro zavření `scope_guard` objektu po bits rastrového obrázku jsou odemčený, ale před odesláním všechny zprávy do vlákna uživatelského rozhraní. To zajistí, že vlákna uživatelského rozhraní není aktualizovány předtím, než jsou odemknout bits rastrového obrázku.  
  
     [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]  
  
9. Ověřte, že aplikace byl úspěšně aktualizován vytváření a jeho spuštěním.  
  
 Když změníte velikost okna, kreslení pracovní se provádí pouze u poslední okno velikost. Všechny aktivní úlohy kreslení také došlo ke zrušení při okno zničena.  
  
 [[Horní](#top)]  
  
## <a name="see-also"></a>Viz také  
 [Návody k Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkce usnadnění](../../parallel/concrt/message-passing-functions.md)   
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)   
 [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)   
 [Běžné aplikace knihovny MFC](../../mfc/mfc-desktop-applications.md)
