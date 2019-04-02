---
title: Závažná chyba C1211
ms.date: 11/04/2016
f1_keywords:
- C1211
helpviewer_keywords:
- C1211
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
ms.openlocfilehash: f39ab027d8d81762ae1cf8f38405f3e21524da2e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781936"
---
# <a name="fatal-error-c1211"></a>Závažná chyba C1211

Vlastní atribut TypeForwardedTo není podporován verzí modulu runtime nainstalovaného

C1211 nastane, pokud máte pro aktuální verzi, ale společného jazykového modulu runtime z předchozí verze kompilátoru.

Některé funkce kompilátoru nemusí fungovat v době běhu předchozí verze.

K vyřešení C1211 instalaci modul common language runtime, dodávané spolu se kompilátor používáte.

Další informace najdete v tématu [předávání typů (C + +/ CLI)](../../extensions/type-forwarding-cpp-cli.md).