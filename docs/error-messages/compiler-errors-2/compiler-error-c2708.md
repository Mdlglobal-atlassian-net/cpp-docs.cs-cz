---
title: Chyba kompilátoru C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a128613cabb201142c29b833959924dbf8a6e0ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160950"
---
# <a name="compiler-error-c2708"></a>Chyba kompilátoru C2708

'identifier': Skutečná délka parametrů v bajtech se liší od předchozího volání nebo odkazu

A [__stdcall](../../cpp/stdcall.md) funkce musí být předcházen prototypu. V opačném případě kompilátor interpretuje první volání funkce jako prototyp a k této chybě dochází, když kompilátor narazí volání, které se neshoduje.

Chcete-li vyřešit tuto chybu přidat prototypu funkce.