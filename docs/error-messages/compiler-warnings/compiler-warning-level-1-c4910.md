---
title: Upozornění (úroveň 1) C4910 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e6db959e467ea449a66feb3ee07c202f4dee002
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018948"
---
# <a name="compiler-warning-level-1-c4910"></a>Kompilátor upozornění (úroveň 1) C4910

"\<identifikátor >": "__declspec(dllexport)" a "externí" nejsou pro explicitní vytváření instancí

Explicitní vytvoření instance šablony s názvem  *\<identifikátor >* je upraven na i `__declspec(dllexport)` a `extern` klíčová slova. Tato klíčová slova jsou však vzájemně vylučují. `__declspec(dllexport)` – Klíčové slovo znamená, že vytvoření instance šablony třídy, zatímco `extern` – klíčové slovo znamená, že automaticky instanci šablony třídy.

## <a name="see-also"></a>Viz také

[Explicitní vytvoření instance](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Obecná pravidla a omezení](../../cpp/general-rules-and-limitations.md)