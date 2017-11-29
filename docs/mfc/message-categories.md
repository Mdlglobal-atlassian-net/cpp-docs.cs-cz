---
title: "Kategorie zpráv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1c7a463e3d2e0f11373c47f66a745c9c486a4581
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="message-categories"></a>Kategorie zpráv
Jaké zprávy napíšete obslužné rutiny pro existují tří kategorií:  
  
1.  zprávy Windows  
  
     To zahrnuje především zprávy, počínaje **WM_** předpona, s výjimkou **wm_command –**. Zprávy Windows zpracovává windows a zobrazení. Tyto zprávy mají často parametry, které jsou použité při určení způsobu zpracování zprávy.  
  
2.  Oznámení ovládacího prvku  
  
     To zahrnuje **wm_command –** zprávy oznámení z ovládacích prvků a dalších podřízená okna do své nadřazené windows. Například ovládací prvek upravit odešle jeho nadřazený objekt **wm_command –** zpráva obsahující **EN_CHANGE** kód oznámení ovládacího prvku, když uživatel trvá akci, která může mít změnit text v textovém poli. Okně obslužné rutiny pro zprávu odpoví na oznámení některé vhodným způsobem, jako je například načítání textu v ovládacím prvku.  
  
     Rozhraní framework směrování zpráv oznámení ovládacího prvku jako jiný **WM_** zprávy. Jedinou výjimkou je však **BN_CLICKED** řízení oznámení zaslaná tlačítka, když uživatel klikne, je. Tato zpráva je zpracováván speciálně jako zprávou příkazu a směrovat jako ostatní příkazy.  
  
3.  Příkaz zprávy  
  
     To zahrnuje **wm_command –** zpráv s oznámením z objektů uživatelského rozhraní: nabídky, tlačítek panelu nástrojů a klávesy akcelerátoru. Rozhraní framework zpracovává příkazy jinak než ostatní zprávy a může zpracovat pomocí další typy objektů, jak je popsáno v [cíle příkazů](../mfc/command-targets.md).  
  
##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a>Zprávy Windows a zpráv s oznámením ovládacího prvku  
 Zprávy v kategoriích 1 a 2 – zpráv systému Windows a oznámení ovládacích prvků – jsou zpracovávány v systému windows: objekty třídy odvozené od třídy `CWnd`. To zahrnuje `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, a vlastní třídy odvozené od těchto základní třídy. Tyto objekty zapouzdřují `HWND`, popisovač pro okno systému Windows.  
  
##  <a name="_core_command_messages"></a>Příkaz zprávy  
 Zprávy v kategorii 3 – příkazy – může zpracovávat širší různé objekty: dokumenty, šablony dokumentů a objektu application kromě windows a zobrazení. Pokud příkaz přímo ovlivňuje některé konkrétní objekt, má smysl mít tento objekt zpracování příkazu. Příkaz Otevřít v nabídce Soubor je třeba logicky spojený s aplikací: aplikace otevře zadaný dokument po přijetí příkazu. Obslužná rutina pro příkaz otevřete tak je funkce člena třídy aplikace. Další informace o příkazech a jak se směrují na objekty najdete v tématu [jakým způsobem volá Framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprávy a příkazy v rozhraní Framework](../mfc/messages-and-commands-in-the-framework.md)
