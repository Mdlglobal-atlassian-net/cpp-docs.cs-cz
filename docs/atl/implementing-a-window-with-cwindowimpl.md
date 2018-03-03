---
title: Implementace okno s CWindowImpl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CWindowImpl
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80aca6af847a33fd7217d0ad710c928f6d2ca32e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implementace okno s CWindowImpl
Pokud chcete implementovat okno, odvození třídy z `CWindowImpl`. Odvozené třídy deklarujte mapy zpráv a funkce obslužných rutin zpráv. Teď můžete použít třídu třemi různými způsoby:  
  
-   [Vytvoření okna založené na novou třídu s Windows](#_atl_creating_a_window_based_on_a_new_windows_class)  
  
-   [Supertřídě existující třídy Windows](#_atl_superclassing_an_existing_windows_class)  
  
-   [Podtřída existujícího okna](#_atl_subclassing_an_existing_window)  
  
##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a>Vytvoření okna založené na novou třídu s Windows  
 `CWindowImpl`obsahuje [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) makro deklarovat informace o třídě systému Windows. Implementuje toto makro `GetWndClassInfo` funkci, která používá [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) zadat informace novou třídu s Windows. Když `CWindowImpl::Create` je volána, tento Windows třída je zaregistrován a vytvořit nové okno.  
  
> [!NOTE]
>  `CWindowImpl`předá **NULL** k `DECLARE_WND_CLASS` makro, což znamená ATL vygeneruje název třídy systému Windows. Chcete-li zadat vlastní název, předejte řetězec tak, aby `DECLARE_WND_CLASS` ve vaší `CWindowImpl`-odvozené třídy.  
  
## <a name="example"></a>Příklad  
 Tady je příklad třídy, která implementuje okno založené na novou třídu Windows:  
  
 [!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]  
  
 Vytvoření okna, vytvořte instanci `CMyWindow` a pak zavolají **vytvořit** metoda.  
  
> [!NOTE]
>  Pokud chcete přepsat výchozí informace o Windows třídy, implementovat `GetWndClassInfo` metoda v odvozené třídě nastavením `CWndClassInfo` členy na odpovídající hodnoty.  
  
##  <a name="_atl_superclassing_an_existing_windows_class"></a>Vytváření supertříd existující třídy Windows  
 [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) makro vám umožní vytvořit okno této nadřazených tříd Windows pro existující třída. Zadejte tento makro ve vaší `CWindowImpl`-odvozené třídy. Jako další okno ATL zprávy jsou zpracovávány mapy zpráv.  
  
 Při použití `DECLARE_WND_SUPERCLASS`, se zaregistruje novou třídu s Windows. Tato nová třída bude stejné jako existující třídy, ale nahradí okno procedura s `CWindowImpl::WindowProc` (nebo s vaší funkce, který přepíše tuto metodu).  
  
## <a name="example"></a>Příklad  
 Následující je příkladem třídu této nadřazených tříd standardní upravit třídy:  
  
 [!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]  
  
 Vytvoření okna superclassed upravit, vytvořte instanci `CMyEdit` a pak zavolají **vytvořit** metoda.  
  
##  <a name="_atl_subclassing_an_existing_window"></a>Vytvoření podtřídy existujícího okna  
 K podtřídami existujícího okna odvození třídy z `CWindowImpl` a mapy zpráv, jako v obou případech předchozí deklarovat. Upozorňujeme však, že nezadáte žádné informace o třídě Windows vzhledem k tomu, že bude podtřídami stávající okno.  
  
 Místo volání **vytvořit**, volání `SubclassWindow` a předejte ji do okna existující chcete podtřídami popisovač. Jakmile podtřídou třídy okna, se bude používat `CWindowImpl::WindowProc` (nebo vaše funkce, který přepíše tuto metodu) směrovat zprávy a pokuste se mapy zpráv. Okno rozčleněné z objektu odpojení, volání `UnsubclassWindow`. Okně původní okno postup potom se obnoví.  
  
## <a name="see-also"></a>Viz také  
 [Implementace okna](../atl/implementing-a-window.md)

