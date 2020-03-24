---
title: Upozornění kompilátoru (úroveň 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: c1de07cd65bbc9f02a979ceebe31be4143af70ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175815"
---
# <a name="compiler-warning-level-1-c4276"></a>Upozornění kompilátoru (úroveň 1) C4276

' function ': není k dispozici žádný prototyp; Nepředpokládat žádné parametry

Když převezmete adresu funkce s konvencí volání [__stdcall](../../cpp/stdcall.md) , je nutné poskytnout prototyp, aby kompilátor mohl vytvořit dekorované jméno funkce. Vzhledem k tomu, že *funkce* nemá žádný prototyp, kompilátor při vytváření dekorované názvu předpokládá, že funkce nemá žádné parametry.
