---
title: Upozornění kompilátoru (úroveň 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: a3f29cb895da8c06ed43dd5c9956426f3f6014f1
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810712"
---
# <a name="compiler-warning-level-1-c4910"></a>Upozornění kompilátoru (úroveň 1) C4910

\<> identifikátoru: __declspec (dllexport) a extern nejsou pro explicitní vytváření instancí kompatibilní.

Explicitní vytváření instancí šablony s názvem *\<> identifikátoru* je upraveno pomocí klíčových slov `__declspec(dllexport)` i `extern`. Tato klíčová slova se však vzájemně vylučují. Klíčové slovo `__declspec(dllexport)` znamená vytvoření instance třídy šablony, zatímco klíčové slovo `extern` znamená, že není automaticky vytvořena instance třídy šablony.

## <a name="see-also"></a>Viz také:

[Explicitní vytvoření instance](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Obecná pravidla a omezení](../../cpp/general-rules-and-limitations.md)