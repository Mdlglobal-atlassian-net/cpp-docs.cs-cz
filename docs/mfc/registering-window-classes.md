---
title: "Registrace tříd oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WndProc
dev_langs: C++
helpviewer_keywords:
- window classes [MFC], registering
- registry [MFC], registering classes
- AfxRegisterWndClass method [MFC]
- MFC, windows
- WinMain method [MFC], and registering window classes
- WndProc method [MFC]
- classes [MFC], registering window classes
- WinMain method [MFC]
- registering window classes [MFC]
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bfcc0cb9459245f4fa6553774ee943555c09d141
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="registering-window-classes"></a>Registrace tříd oken
Okno "třídy" v tradiční programování pro systém Windows definovat vlastnosti "třída" (ne C++ třídu) ze kterého můžete vytvořit libovolný počet systému windows. Tento typ třídy je šablony nebo model pro vytváření systému windows.  
  
## <a name="window-class-registration-in-traditional-programs-for-windows"></a>Registrace tříd oken v tradiční programy pro Windows  
 V tradiční programu pro systém Windows bez MFC, zpracovávat všechny zprávy do okna v jeho "okno postupu" nebo "**WndProc**." A **WndProc** je přidružen období prostřednictvím procesu "registrace tříd oken". Hlavní okno je zaregistrován v `WinMain` funkce, ale ostatní třídy systému windows se dají registrovat kdekoli v aplikaci. Registrace závisí na strukturu, která obsahuje odkazy **WndProc** fungovat společně s specifikace pro kurzor, štětec pozadí plochy a tak dále. Struktura je předán jako parametr, společně s název řetězce objektu třídy, v předchozí volání **RegisterClass** funkce. Registrace třídy proto může být sdílen více oken.  
  
## <a name="window-class-registration-in-mfc-programs"></a>Registrace tříd oken v aplikacích MFC  
 Většina činnost registrace třídy oken, se provádí automaticky v aplikaci MFC framework. Pokud používáte MFC, obvykle odvození třídy oken C++ z existující třídy knihovny pomocí normální syntaxe C++ pro dědičnosti tříd. Rozhraní framework dál používá tradiční "registrace třídy" a poskytuje několik standardní ty registrované pro vás v případě potřeby. Můžete registrovat další registrace třídy voláním [afxregisterwndclass –](../mfc/reference/application-information-and-management.md#afxregisterwndclass) globální funkce a následné předání registrované třídy **vytvořit** členské funkce `CWnd`. Podle postupu popsaného tady, tradiční "registrace třída" v systému Windows je termín nelze zaměňovat s třídami C++.  
  
 Další informace najdete v tématu [Technická poznámka 1](../mfc/tn001-window-class-registration.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytváření oken](../mfc/creating-windows.md)
