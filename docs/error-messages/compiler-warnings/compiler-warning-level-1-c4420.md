---
title: Upozornění kompilátoru (úroveň 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: 72ab87b34e07717112f5af1727a216b4f786ae0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186787"
---
# <a name="compiler-warning-level-1-c4420"></a>Upozornění kompilátoru (úroveň 1) C4420

' operator ': operátor není k dispozici, místo toho použijte operátor ' operator '; může dojít k ohrožení zabezpečení při kontrole za běhu.

Toto upozornění je generováno při použití [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (Vector New/Delete prověřování) a v případě, že není nalezeno žádné vektorové formuláře. V tomto případě je použit nevektorový formulář.

Aby/RTCv fungovalo správně, kompilátor by měl vždy volat vektorovou formu [new](../../cpp/new-operator-cpp.md)/[Odstranit](../../cpp/delete-operator-cpp.md) , pokud byla použita syntaxe Vector.
