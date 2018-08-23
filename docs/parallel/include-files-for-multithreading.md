---
title: Zahrnuté soubory pro Multithreading | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73444c72878073d881abec08c474eb1f1ce64f02
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42466385"
---
# <a name="include-files-for-multithreading"></a>Zahrnuté soubory pro multithreading
Standardní vložené soubory deklarujte funkce knihovny run-time jazyka C, jak jsou implementované v knihovnách. Pokud používáte [úplná optimalizace](../build/reference/ox-full-optimization.md) (/ Ox) nebo [fastcall konvence volání](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) možnost, kompilátor předpokládá, že všechny funkce lze volat pomocí registru konvence volání. Funkce knihovny run-time byly zkompilovány pomocí konvence volání jazyka C a že bude kompilátor generovat správný externí odkazy na tyto funkce se deklarace ve standardních vložených souborech.  
  
## <a name="see-also"></a>Viz také  

[Multithreading s použitím jazyka C a prostředí Win32](../parallel/multithreading-with-c-and-win32.md)