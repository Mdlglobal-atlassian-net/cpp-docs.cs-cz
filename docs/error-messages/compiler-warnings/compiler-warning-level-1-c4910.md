---
title: Kompilátor upozornění (úroveň 1) C4910
ms.date: 11/04/2016
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: f0d1df0a383b6646d52fc2babc53ca656d49ace6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428194"
---
# <a name="compiler-warning-level-1-c4910"></a>Kompilátor upozornění (úroveň 1) C4910

"\<identifikátor >": "__declspec(dllexport)" a "externí" nejsou pro explicitní vytváření instancí

Explicitní vytvoření instance šablony s názvem  *\<identifikátor >* je upraven na i `__declspec(dllexport)` a `extern` klíčová slova. Tato klíčová slova jsou však vzájemně vylučují. `__declspec(dllexport)` – Klíčové slovo znamená, že vytvoření instance šablony třídy, zatímco `extern` – klíčové slovo znamená, že automaticky instanci šablony třídy.

## <a name="see-also"></a>Viz také

[Explicitní vytvoření instance](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Obecná pravidla a omezení](../../cpp/general-rules-and-limitations.md)