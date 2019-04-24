---
title: type_info – třída
ms.date: 11/04/2016
f1_keywords:
- type_info
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
ms.openlocfilehash: 169a54373c66c2f6b33d71e68500c3bf85e871c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266826"
---
# <a name="typeinfo-class"></a>type_info – třída

**Type_info** třída popisuje typ informace generované kompilátorem v rámci programu. Objekty této třídy účinně ukládají ukazatel na název typu. **Type_info** třídy také ukládá kódovanou hodnotu vhodnou pro porovnání dvou typů pro rovnost nebo pořadí řazení. Pravidla kódování a pořadí řazení typů nejsou specifikována a mezi programy se mohou lišit.

`<typeinfo>` Soubor hlaviček musí být zahrnut pro použití **type_info** třídy. Rozhraní pro **type_info** třída je:

```cpp
class type_info {
public:
    virtual ~type_info();
    size_t hash_code() const
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;
    _CRTIMP_PURE int before(const type_info& rhs) const;
    _CRTIMP_PURE const char* name() const;
    _CRTIMP_PURE const char* raw_name() const;
};
```

Nelze vytvořit instanci objektů **type_info** třídy přímo, protože tato třída má pouze soukromý kopírovací konstruktor. Jediný způsob, jak vytvořit (dočasný) **type_info** objektu je použít [typeid](../cpp/typeid-operator.md) operátor. Protože operátor přiřazení je také soukromý, nelze kopírovat ani přiřadit objekty třídy **type_info**.

`type_info::hash_code` Definuje funkci hash, která je vhodná pro mapování hodnot typu **typeinfo** k distribuci hodnot indexu.

Operátory `==` a `!=` slouží k porovnání rovnosti a nerovnosti s jinými **type_info** objekty v uvedeném pořadí.

Neexistuje žádná souvislost mezi pořadím řazení typů a vztahy dědičnosti. Použití `type_info::before` členskou funkci k určení pořadí řazení typů. Neexistuje žádná záruka, který `type_info::before` předá stejné výsledky v různých programech nebo dokonce během různých spuštění stejného programu. Tímto způsobem `type_info::before` je podobný adresy `(&)` operátor.

`type_info::name` Členská funkce vrátí `const char*` na řetězec zakončený hodnotou null představující čitelný název typu. Paměť, na kterou je odkazováno, je uložena do mezipaměti a neměla by nikdy být odebrána přímo.

`type_info::raw_name` Členská funkce vrátí `const char*` na řetězec zakončený hodnotou null představující upravený název typu objektu. Ve skutečnosti je název pro úsporu místa uložen v upravené podobě. V důsledku toho tato funkce je rychlejší než `type_info::name` protože není nutné rušit úpravu názvu. Řetězec vrácený funkcí `type_info::raw_name` funkce je užitečný v operacích porovnávání, ale není čitelný. Pokud potřebujete řetězec čitelný, použijte `type_info::name` namísto toho funkci.

Informace o typu se generuje pro polymorfní třídy pouze tehdy, pokud [/GR (povolení běhové informace o typu)](../build/reference/gr-enable-run-time-type-information.md) je zadána možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[Informace o typu modulu runtime](../cpp/run-time-type-information.md)