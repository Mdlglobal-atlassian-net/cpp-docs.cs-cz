---
title: Závažná chyba C1211 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1211
dev_langs:
- C++
helpviewer_keywords:
- C1211
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 444d2bc25c2eddd5ea9a0170272bd3e71b61f94f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018521"
---
# <a name="fatal-error-c1211"></a>Závažná chyba C1211

Vlastní atribut TypeForwardedTo není podporován verzí modulu runtime nainstalovaného

C1211 nastane, pokud máte pro aktuální verzi, ale společného jazykového modulu runtime z předchozí verze kompilátoru.

Některé funkce kompilátoru nemusí fungovat v době běhu předchozí verze.

K vyřešení C1211 instalaci modul common language runtime, dodávané spolu se kompilátor používáte.

Další informace najdete v tématu [předávání typů (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).