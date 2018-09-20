---
title: Registrace tříd oken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- WndProc
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dca6b7753ad3fd4024cadb899652336fa2f860b5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403094"
---
# <a name="registering-window-classes"></a>Registrace tříd oken

"Třídy okna" v tradiční programování pro Windows definovat vlastnosti "třída" (ne třídu jazyka C++) ze které lze vytvořit libovolný počet systému windows. Tento typ třídy je šablona nebo model pro vytváření oken.

## <a name="window-class-registration-in-traditional-programs-for-windows"></a>Registrace tříd oken v tradičních aplikacích pro Windows

Tradiční aplikace pro Windows bez knihovny MFC, zpracovávat všechny zprávy do okna v jeho "proceduru okna" nebo "`WndProc`." A `WndProc` souvisí s oknem prostřednictvím procesu "registrace tříd oken". Hlavní okno je registrován v `WinMain` funkce, ale jiné třídy windows mohou být registrovány kdekoli v aplikaci. Registrace závisí na strukturu, která obsahuje ukazatel `WndProc` fungovat společně s specifikace kurzoru štětec pozadí a tak dále. Struktura je předán jako parametr, spolu s názvem řetězec třídy v předchozím volání `RegisterClass` funkce. Registrace třídy proto může být sdílen více oken.

## <a name="window-class-registration-in-mfc-programs"></a>Registrace tříd oken v aplikacích MFC

Většina činnost registrace třídy okna naproti tomu je prováděno automaticky v rozhraní framework aplikace MFC. Pokud používáte knihovnu MFC, obvykle odvodit třídu okna C++ z existující třídy knihovny prostřednictvím normální syntaxe C++ dědičnost tříd. Rozhraní stále používá tradiční "registrace třídy" a poskytuje několik standardních ty, které jsou registrovány pro vás v případě potřeby. Můžete zaregistrovat další registraci třídy voláním [afxregisterwndclass –](../mfc/reference/application-information-and-management.md#afxregisterwndclass) globální funkce a následným předáním registrované třídy, která se `Create` členskou funkci `CWnd`. Podle postupu popsaného tady, tradiční "registrace třídy" ve Windows se by se zaměňovat s třídou C++.

Další informace najdete v tématu [Technická poznámka 1](../mfc/tn001-window-class-registration.md).

## <a name="see-also"></a>Viz také

[Vytváření oken](../mfc/creating-windows.md)

