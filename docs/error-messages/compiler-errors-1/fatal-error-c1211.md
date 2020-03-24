---
title: Závažná chyba C1211
ms.date: 11/04/2016
f1_keywords:
- C1211
helpviewer_keywords:
- C1211
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
ms.openlocfilehash: 1e01f75877169225d0e6c20b8a36ce55e3c15c4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203369"
---
# <a name="fatal-error-c1211"></a>Závažná chyba C1211

Vlastní atribut TypeForwardedTo není podporován nainstalovanou verzí modulu runtime.

K C1211 dojde, když máte kompilátor pro aktuální vydání, ale modul CLR (Common Language Runtime) z předchozí verze.

Některé funkce kompilátoru nemusí fungovat v předchozí verzi doby běhu.

Pro vyřešení C1211 nainstalujte modul CLR (Common Language Runtime), který byl dodán s kompilátorem, který používáte.

Další informace naleznete v tématu [předávání typů (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).
