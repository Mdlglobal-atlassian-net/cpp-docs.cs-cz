---
title: Kompilátor upozornění (úroveň 1) C4910
ms.date: 11/04/2016
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: 49cbbf3369fc4765d93e67e2dca84a4d975560d7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027548"
---
# <a name="compiler-warning-level-1-c4910"></a>Kompilátor upozornění (úroveň 1) C4910

"\<identifikátor >": "__declspec(dllexport)" a "externí" nejsou pro explicitní vytváření instancí

Explicitní vytvoření instance šablony s názvem  *\<identifikátor >* je upraven na i `__declspec(dllexport)` a `extern` klíčová slova. Tato klíčová slova jsou však vzájemně vylučují. `__declspec(dllexport)` – Klíčové slovo znamená, že vytvoření instance šablony třídy, zatímco `extern` – klíčové slovo znamená, že automaticky instanci šablony třídy.

## <a name="see-also"></a>Viz také:

[Explicitní vytvoření instance](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Obecná pravidla a omezení](../../cpp/general-rules-and-limitations.md)