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
ms.openlocfilehash: ec531c2c0eeac14a617a3e0e3b450cf467808165
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2018
ms.locfileid: "43130765"
---
# <a name="include-files-for-multithreading"></a>Zahrnuté soubory pro multithreading
Standardní vložené soubory deklarujte funkce knihovny run-time jazyka C, jak jsou implementované v knihovnách. Pokud používáte [úplná optimalizace](../build/reference/ox-full-optimization.md) (/ Ox) nebo [fastcall konvence volání](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) možnost, kompilátor předpokládá, že všechny funkce lze volat pomocí registru konvence volání. Funkce knihovny run-time byly zkompilovány pomocí konvence volání jazyka C a že bude kompilátor generovat správný externí odkazy na tyto funkce se deklarace ve standardních vložených souborech.  
  
## <a name="see-also"></a>Viz také  

[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)