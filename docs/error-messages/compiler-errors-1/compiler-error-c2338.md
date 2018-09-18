---
title: Chyba kompilátoru C2338 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2338
dev_langs:
- C++
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77bc98afdad36e0505abb58ee06ec1c7e7654ae5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071572"
---
# <a name="compiler-error-c2338"></a>Chyba kompilátoru C2338

> *Chybová zpráva*

Tuto chybu může způsobovat `static_assert` chyby během kompilace. Poskytl se zpráva `static_assert` parametry.

Tato chybová zpráva může být také generován externí zprostředkovatele pro kompilátor. Ve většině případů jsou tyto chyby ohlásil podle poskytovatele atributu knihovny DLL, jako je například ATLPROV. Některé běžné formuláře této zprávy zahrnout:

> "*atribut*" atribut poskytovatele Atl: Chyba ATL*číslo* *zprávy*

> Nesprávné použití atributu '*atribut*.

> "*využití*': nesprávný formát pro atribut 'využití.

Tyto chyby jsou často neopravitelné a může být následován znakem závažná chyba kompilátoru.

Chcete-li vyřešit tyto problémy, opravte použití atributu. V některých případech, například musí být parametry atributu deklarována před jejich použitím. Pokud číslo chyby knihovny ATL naleznete v dokumentaci k této chybě konkrétnější informace.
