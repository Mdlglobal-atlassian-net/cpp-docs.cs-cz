---
title: Závažná chyba C1210
ms.date: 11/04/2016
f1_keywords:
- C1210
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
ms.openlocfilehash: 50bafa522c931c909b5ce163a78305ffc028765a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203382"
---
# <a name="fatal-error-c1210"></a>Závažná chyba C1210

> /CLR: Pure a/CLR: safe nejsou podporované nainstalovanou verzí modulu runtime.

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

K C1210 dojde, když máte kompilátor pro aktuální vydání, ale modul CLR (Common Language Runtime) z předchozí verze.

Některé funkce kompilátoru nemusí fungovat v předchozí verzi doby běhu.

Chcete-li vyřešit C1210, nainstalujte verzi modulu Common Language Runtime, která je určena pro použití s vaším kompilátorem.
