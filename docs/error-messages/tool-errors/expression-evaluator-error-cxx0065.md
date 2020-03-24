---
title: Chyba při vyhodnocování výrazu CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: b4120deec3c8e7ce14e381f782904cf83a588e43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184421"
---
# <a name="expression-evaluator-error-cxx0065"></a>Chyba při vyhodnocování výrazu CXX0065

Proměnná vyžaduje rámec zásobníku.

Výraz obsahoval proměnnou, která existuje v rámci aktuálního oboru, ale ještě nebyla vytvořena.

K této chybě může dojít, pokud jste se přeměnili na prolog funkce, ale ještě jste nastavili rámec zásobníku pro funkci, nebo pokud jste se změnili na ukončovací kód funkce.

Projděte si kód prologu, dokud není před vyhodnocením výrazu nastavený rámec zásobníku.

Tato chyba je shodná s CAN0065.
