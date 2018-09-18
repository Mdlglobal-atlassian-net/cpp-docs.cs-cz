---
title: registrace – specifikátor třídy úložiště | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e15b6bd4136e2644dbd040ac509b35af772ae4c3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028321"
---
# <a name="register-storage-class-specifier"></a>register – specifikátor třídy úložiště

**Specifické pro Microsoft**

Kompilátor jazyka C/C++ společnosti Microsoft nerespektuje požadavky uživatele na proměnné registru. Ale pro přenositelnost všechny ostatní sémantiky přidružené **zaregistrovat** – klíčové slovo jsou kompilátorem respektovány. Například nelze použít unární address-of – operátor (**&**) na objekt registru ani použít **zaregistrovat** klíčové slovo se používá pro pole.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Specifikátory třídy úložiště pro deklarace na interní úrovni](../c-language/storage-class-specifiers-for-internal-level-declarations.md)