---
title: Zahrnuté soubory pro multithreading
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
ms.openlocfilehash: 79b5c56eecfaf28743eec4ba6b4cee56156d6e2c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257420"
---
# <a name="include-files-for-multithreading"></a>Zahrnuté soubory pro multithreading

Standardní vložené soubory deklarujte funkce knihovny run-time jazyka C, jak jsou implementované v knihovnách. Pokud používáte [úplná optimalizace](../build/reference/ox-full-optimization.md) (/ Ox) nebo [fastcall konvence volání](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) možnost, kompilátor předpokládá, že všechny funkce lze volat pomocí registru konvence volání. Funkce knihovny run-time byly zkompilovány pomocí konvence volání jazyka C a že bude kompilátor generovat správný externí odkazy na tyto funkce se deklarace ve standardních vložených souborech.

## <a name="see-also"></a>Viz také:

[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)
