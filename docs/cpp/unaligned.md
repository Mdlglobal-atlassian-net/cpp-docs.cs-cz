---
title: __unaligned | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9593a0b3c6e6980f5be2ce9dcf13e505e94dcace
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040192"
---
# <a name="unaligned"></a>__unaligned

**Specifické pro Microsoft**. Při deklaraci ukazatele s **__unaligned** modifikátor, kompilátor předpokládá, že ukazatel odkazuje na data, která nejsou zarovnána. V důsledku toho příslušné platformy kód je generován pro zpracování nezarovnaných čtení a zapíše prostřednictvím ukazatele.

## <a name="remarks"></a>Poznámky

Tento modifikátor popisuje zarovnání dat adresovaný ukazatelem; ukazatel sám je považován za zarovnaný.

Nutnost **__unaligned** – klíčové slovo se liší podle platformy a prostředí. Nepodařilo se označit data správně může dojít k problémům s od snížení výkonu na hardwarových chyb. **__Unaligned** modifikátor není platný pro x86 platformy.

Další informace o zarovnání naleznete v následujících tématech:

- [align](../cpp/align-cpp.md)

- [__alignof – operátor](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md)

- [Příklady zarovnání struktur](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)