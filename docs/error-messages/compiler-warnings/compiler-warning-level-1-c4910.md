---
title: Upozornění kompilátoru (úroveň 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: dc5feb3613e45134a08e493b397eb738fffee8a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174775"
---
# <a name="compiler-warning-level-1-c4910"></a>Upozornění kompilátoru (úroveň 1) C4910

\<> identifikátoru: __declspec (dllexport) a extern nejsou pro explicitní vytváření instancí kompatibilní.

Explicitní vytváření instancí šablony s názvem *\<> identifikátoru* je upraveno pomocí klíčových slov `__declspec(dllexport)` i `extern`. Tato klíčová slova se však vzájemně vylučují. Klíčové slovo `__declspec(dllexport)` znamená vytvoření instance třídy šablony, zatímco klíčové slovo `extern` znamená, že není automaticky vytvořena instance třídy šablony.

## <a name="see-also"></a>Viz také

[Explicitní vytvoření instance](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Obecná pravidla a omezení](../../cpp/general-rules-and-limitations.md)
