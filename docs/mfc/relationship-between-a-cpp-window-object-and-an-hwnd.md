---
title: "Vztah mezi objektem okna v jazyku C++ a popisovačem HWND | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HWND
dev_langs: C++
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7f6e9da311a4141f50c49c8096ef9f0c95493c73
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Vztah mezi objektem okna v jazyku C++ a popisovačem HWND
Okno *objekt* je objekt C++ `CWnd` – třída (nebo v odvozené třídě) přímo vytvářející vašeho programu. Se dodává a přejde na základě vašeho programu konstruktor a destruktor výzvy. Windows *okno*, na druhé straně je neprůhledného popisovače vnitřní datovou strukturu Windows, který odpovídá okno a spotřebovává prostředky systému, pokud jsou k dispozici. Okno systému Windows je identifikována "popisovač okna" (`HWND`) a je vytvořen po `CWnd` objekt se vytvoří voláním **vytvořit** funkce člena třídy `CWnd`. Okno může být zničený, volání programu nebo akce uživatele. Popisovač okna je uložený v objektu okna `m_hWnd` členské proměnné. Následující obrázek znázorňuje vztah mezi objektem okna C++ a období systému Windows. Vytváření windows je popsáno v [vytváření Windows](../mfc/creating-windows.md). Zničení oken popsané v [zničení objektů oken](../mfc/destroying-window-objects.md).  
  
 ![CWnd objektu okna a výsledný okna](../mfc/media/vc37fj1.gif "vc37fj1")  
Okno objekt a Windows – okno  
  
## <a name="see-also"></a>Viz také  
 [Objekty oken](../mfc/window-objects.md)
