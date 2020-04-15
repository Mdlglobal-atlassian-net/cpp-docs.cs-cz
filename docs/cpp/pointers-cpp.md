---
title: Ukazatelé (C++)
ms.date: 11/19/2019
description: O nezpracovaných ukazatelích a inteligentních ukazatelích v jazyce Microsoft C++.
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 485cee667fa288bff76fdeac7c9f229355c276d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371921"
---
# <a name="pointers-c"></a>Ukazatelé (C++)

Ukazatel je proměnná, která ukládá adresu paměti objektu. Ukazatele se používají ve velké míře v jazyce C a C++ pro tři hlavní účely:

- přidělit nové objekty na haldě,
- předat funkce dalším funkcím
- iterát přes prvky v polích nebo jiných datových struktur.

V programování ve stylu Jazyka C jsou pro všechny tyto scénáře *použity nezpracované ukazatele.* Nezpracované ukazatele jsou však zdrojem mnoha závažných chyb programování. Proto jejich použití důrazně nedoporučuje s výjimkou, kde poskytují významné výhody výkonu a neexistuje žádná nejednoznačnost, který ukazatel je *vlastnící ukazatel,* který je zodpovědný za odstranění objektu. Moderní C++ poskytuje *inteligentní ukazatele* pro přidělování objektů, *iterátory* pro procházení datových struktur a *lambda výrazy* pro předávání funkcí. Pomocí těchto jazykových a knihovních zařízení namísto nezpracovaných ukazatelů zajistíte, že program bude bezpečnější, snadněji laditelný a snadněji pochopit a udržovat. Další informace naleznete [v tématu Inteligentní ukazatele](smart-pointers-modern-cpp.md), [Výrazy Iterátory](../standard-library/iterators.md)a [Lambda.](lambda-expressions-in-cpp.md)

## <a name="in-this-section"></a>V tomto oddílu

- [Nezpracované ukazatele](raw-pointers.md)
- [Const a těkavé ukazatele](const-and-volatile-pointers.md)
- [nové a odstranit operátory](new-and-delete-operators.md)
- [Chytré ukazatele](smart-pointers-modern-cpp.md)
- [Postup: Vytvoření a použití unique_ptr instancí](how-to-create-and-use-unique-ptr-instances.md)
- [Postup: Vytvoření a použití shared_ptr instancí](how-to-create-and-use-shared-ptr-instances.md)
- [Postup: Vytvoření a použití weak_ptr instancí](how-to-create-and-use-weak-ptr-instances.md)
- [Postup: Vytvoření a použití instancí CComPtr a CComQIPtr](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>Viz také

[Iterátory](../standard-library/iterators.md)</br>
[Výrazy lambda](lambda-expressions-in-cpp.md)
