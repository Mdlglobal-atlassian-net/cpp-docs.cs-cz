---
title: __unaligned
ms.date: 12/17/2018
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
ms.openlocfilehash: 8eb1b93aa55601125600b6c69d9bff3d9ca43aa3
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626861"
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

- [Příklady zarovnání struktur](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)