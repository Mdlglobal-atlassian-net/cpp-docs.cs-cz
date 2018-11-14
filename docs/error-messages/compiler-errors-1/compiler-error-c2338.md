---
title: Chyba kompilátoru C2338
ms.date: 11/04/2016
f1_keywords:
- C2338
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
ms.openlocfilehash: 2a76ecaf78b117b0c1acabd9fcd50c9ae0f73b98
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332059"
---
# <a name="compiler-error-c2338"></a>Chyba kompilátoru C2338

> *Chybová zpráva*

Tuto chybu může způsobovat `static_assert` chyby během kompilace. Poskytl se zpráva `static_assert` parametry.

Tato chybová zpráva může být také generován externí zprostředkovatele pro kompilátor. Ve většině případů jsou tyto chyby ohlásil podle poskytovatele atributu knihovny DLL, jako je například ATLPROV. Některé běžné formuláře této zprávy zahrnout:

- "*atribut*" atribut poskytovatele Atl: Chyba ATL*číslo* *zprávy*

- Nesprávné použití atributu '*atribut*.

- "*využití*': nesprávný formát pro atribut 'využití.

Tyto chyby jsou často neopravitelné a může být následován znakem závažná chyba kompilátoru.

Chcete-li vyřešit tyto problémy, opravte použití atributu. V některých případech, například musí být parametry atributu deklarována před jejich použitím. Pokud číslo chyby knihovny ATL naleznete v dokumentaci k této chybě konkrétnější informace.
