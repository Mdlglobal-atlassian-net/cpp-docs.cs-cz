---
title: Chyba kompilátoru C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a1d3379a0da42c5aabd38cffbf6f6a3f340ef3b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202368"
---
# <a name="compiler-error-c2708"></a>Chyba kompilátoru C2708

' identifier ': skutečná délka parametrů v bajtech se liší od předchozího volání nebo odkazu

[__Stdcall](../../cpp/stdcall.md) funkce musí předcházet prototypu. V opačném případě kompilátor interpretuje první volání funkce jako prototyp a tato chyba nastane, když kompilátor narazí na volání, které se neshoduje.

Chcete-li tuto chybu opravit, přidejte prototyp funkce.
