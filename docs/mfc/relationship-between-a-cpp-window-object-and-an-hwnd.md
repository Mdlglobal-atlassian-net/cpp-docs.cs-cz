---
title: Vztah mezi objektem okna v jazyku C++ a popisovačem HWND | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- HWND
dev_langs:
- C++
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 844f62b110f54ba3e2c8909a78d58c9f2c01dcac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392811"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Vztah mezi objektem okna v jazyku C++ a popisovačem HWND

V okně *objekt* je objekt jazyka c++ `CWnd` třídy (nebo z odvozené třídy), který vytvoří váš program přímo. Přichází a přejde v reakci na váš program volá konstruktor a destruktor. Windows *okno*, na druhé straně je neprůhledný popisovač vnitřní datovou strukturu Windows, který odpovídá okna a využívá systémové prostředky, pokud je k dispozici. Okno Windows je identifikován "popisovač okna" (`HWND`) a je vytvořen po `CWnd` objekt je vytvořen voláním `Create` členské funkce třídy `CWnd`. V okně může zničit volání programu nebo akce uživatele. Popisovač okna je uložena v objektu window *m_hWnd* členské proměnné. Následující obrázek ukazuje vztah mezi objektem okna C++ a v okně Windows. Vytváření oken je podrobněji popsána [vytváření Windows](../mfc/creating-windows.md). Zničení oken je podrobněji popsána [zničení objektů oken](../mfc/destroying-window-objects.md).

![CWnd objekt okna a okna výsledný](../mfc/media/vc37fj1.gif "vc37fj1") objekt okna a okna Windows

## <a name="see-also"></a>Viz také

[Objekty oken](../mfc/window-objects.md)

