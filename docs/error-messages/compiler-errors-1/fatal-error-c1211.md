---
title: Závažná chyba C1211
ms.date: 11/04/2016
f1_keywords:
- C1211
helpviewer_keywords:
- C1211
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
ms.openlocfilehash: 01b9dbc63ec4dee7335579c4805d34b4ff7214fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534391"
---
# <a name="fatal-error-c1211"></a>Závažná chyba C1211

Vlastní atribut TypeForwardedTo není podporován verzí modulu runtime nainstalovaného

C1211 nastane, pokud máte pro aktuální verzi, ale společného jazykového modulu runtime z předchozí verze kompilátoru.

Některé funkce kompilátoru nemusí fungovat v době běhu předchozí verze.

K vyřešení C1211 instalaci modul common language runtime, dodávané spolu se kompilátor používáte.

Další informace najdete v tématu [předávání typů (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).