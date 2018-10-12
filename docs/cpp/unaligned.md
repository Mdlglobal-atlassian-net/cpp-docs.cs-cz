---
title: __unaligned | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/10/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 444bc3372b22676cacb3ee89b9c0ad92000cedcc
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161213"
---
# <a name="unaligned"></a>__unaligned

**Specifické pro Microsoft**. Při deklaraci ukazatele s **__unaligned** modifikátor, kompilátor předpokládá, že ukazatel odkazuje na data, která nejsou zarovnána. V důsledku toho příslušné platformy kód je generován pro zpracování nezarovnaných čtení a zapíše prostřednictvím ukazatele.

## <a name="remarks"></a>Poznámky

Tento modifikátor popisuje zarovnání dat adresovaný ukazatelem; ukazatel sám je považován za zarovnaný.

Nutnost **__unaligned** – klíčové slovo se liší podle platformy a prostředí. Nepodařilo se označit data správně může dojít k problémům s od snížení výkonu na hardwarových chyb. **__Unaligned** modifikátor není platný pro x86 platformy.

Z důvodu kompatibility s předchozími verzemi **_unaligned** je synonymum pro **__unaligned** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) je zadán.

Další informace o zarovnání naleznete v následujících tématech:

- [align](../cpp/align-cpp.md)

- [__alignof – operátor](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md)

- [Příklady zarovnání struktur](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)