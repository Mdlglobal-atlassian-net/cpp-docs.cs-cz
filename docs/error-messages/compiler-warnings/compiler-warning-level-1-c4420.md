---
title: Kompilátor upozornění (úroveň 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: a4a7e91e7845cc0fc25d5a6fad16ae7b7e327952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408170"
---
# <a name="compiler-warning-level-1-c4420"></a>Kompilátor upozornění (úroveň 1) C4420

'operator': operátor není k dispozici, místo toho; pomocí 'operator' kontrolu za běhu může dojít k ohrožení

Toto upozornění je generováno, když použijete [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector kontroluje nových/delete) a když nenajde žádný formulář vektoru. V takovém případě se používá bez vektoru formuláře.

Aby /RTCv fungovala správně, musí kompilátor vždy volat vektoru formu [nové](../../cpp/new-operator-cpp.md)/[odstranit](../../cpp/delete-operator-cpp.md) Pokud byla použita syntaxe vektoru.