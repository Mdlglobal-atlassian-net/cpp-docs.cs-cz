---
title: register – specifikátor třídy úložiště
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 339a96e33e186ddcc0615f89ff68a7f87b0bfdc7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668647"
---
# <a name="register-storage-class-specifier"></a>register – specifikátor třídy úložiště

**Specifické pro Microsoft**

Kompilátor jazyka C/C++ společnosti Microsoft nerespektuje požadavky uživatele na proměnné registru. Ale pro přenositelnost všechny ostatní sémantiky přidružené **zaregistrovat** – klíčové slovo jsou kompilátorem respektovány. Například nelze použít unární address-of – operátor (**&**) na objekt registru ani použít **zaregistrovat** klíčové slovo se používá pro pole.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Specifikátory třídy úložiště pro deklarace na interní úrovni](../c-language/storage-class-specifiers-for-internal-level-declarations.md)