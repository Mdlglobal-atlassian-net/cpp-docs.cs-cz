---
title: Ukazatele (C++)
ms.date: 11/19/2019
description: O nezpracovaných ukazatelích a inteligentních ukazatelích v Microsoftu C++.
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 21dcc55048e9e378f370f25254e1910b05e49d69
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246420"
---
# <a name="pointers-c"></a>Ukazatele (C++)

Ukazatel je proměnná, která ukládá adresu paměti objektu. Ukazatele se používají rozsáhle v C i C++ pro tři hlavní účely:

- Chcete-li přidělit nové objekty haldě,
- předání funkcí jiným funkcím
- pro iteraci prvků v polích nebo jiných datových strukturách.

V programování ve stylu jazyka C se *nezpracované ukazatele* používají pro všechny tyto scénáře. Nezpracované ukazatele jsou však zdrojem mnoha závažných chyb při programování. Proto jejich použití se důrazně nedoporučuje, s výjimkou případů, kdy poskytují významný přínos výkonu a nedochází k nejednoznačnosti, jako je ukazatel *vlastnící ukazatel* , který je zodpovědný za odstranění objektu. Moderní C++ poskytuje *inteligentní ukazatele* pro přidělování objektů, *iterátorů* pro procházení datových struktur a *výrazy lambda* pro předávání funkcí. Pomocí těchto funkcí jazyka a knihovny namísto nezpracovaných ukazatelů zajistíte bezpečnější a jednodušší ladění a pochopení a údržbu. Další informace najdete v tématu [inteligentní ukazatele](smart-pointers-modern-cpp.md), [iterátory](../standard-library/iterators.md)a [výrazy lambda](lambda-expressions-in-cpp.md) .

## <a name="in-this-section"></a>V tomto oddílu

- [Nezpracované ukazatele](raw-pointers.md)
- [Ukazatele const a volatile](const-and-volatile-pointers.md)
- [operátory New a DELETE](new-and-delete-operators.md)
- [Inteligentní ukazatele](smart-pointers-modern-cpp.md)
- [Postupy: vytváření a používání instancí unique_ptr](how-to-create-and-use-unique-ptr-instances.md)
- [Postupy: vytváření a používání instancí shared_ptr](how-to-create-and-use-shared-ptr-instances.md)
- [Postupy: vytváření a používání instancí weak_ptr](how-to-create-and-use-weak-ptr-instances.md)
- [Postupy: vytváření a používání instancí CComPtr a CComQIPtr](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>Viz také:

[Iterátory](../standard-library/iterators.md)</br>
[Výrazy lambda](lambda-expressions-in-cpp.md)
