---
title: type_info – třída
ms.date: 11/04/2016
f1_keywords:
- type_info
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
ms.openlocfilehash: 7a016fe8fee4e5765e6172184bfa9c90eecbc687
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160668"
---
# <a name="type_info-class"></a>type_info – třída

Třída **type_info** popisuje informace o typu vygenerované v rámci programu kompilátorem. Objekty této třídy účinně ukládají ukazatel na název typu. Třída **type_info** také ukládá kódovanou hodnotu vhodnou pro porovnávání dvou typů pro rovnost nebo pořadí řazení. Pravidla kódování a pořadí řazení typů nejsou specifikována a mezi programy se mohou lišit.

Aby bylo možné použít třídu **type_info** , musí být zahrnut soubor hlaviček `<typeinfo>`. Rozhraní pro třídu **type_info** je:

```cpp
class type_info {
public:
    type_info(const type_info& rhs) = delete; // cannot be copied
    virtual ~type_info();
    size_t hash_code() const;
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;
    type_info& operator=(const type_info& rhs) = delete; // cannot be copied
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;
    _CRTIMP_PURE int before(const type_info& rhs) const;
    size_t hash_code() const noexcept;
    _CRTIMP_PURE const char* name() const;
    _CRTIMP_PURE const char* raw_name() const;
};
```

Nemůžete vytvořit instanci objektů třídy **type_info** přímo, protože třída má pouze privátní kopírovací konstruktor. Jediným způsobem, jak vytvořit (dočasný) **type_info** objekt, je použít operátor [typeid](../cpp/typeid-operator.md) . Vzhledem k tomu, že operátor přiřazení je také soukromý, nelze kopírovat nebo přiřazovat objekty třídy **type_info**.

`type_info::hash_code` definuje funkci hash vhodnou pro mapování hodnot typu **TypeInfo** na distribuci hodnot indexu.

Operátory `==` a `!=` lze použít k porovnání rovnosti a nerovnosti s jinými objekty **type_info** v uvedeném pořadí.

Neexistuje žádná souvislost mezi pořadím řazení typů a vztahy dědičnosti. K určení pořadí řazení typů použijte členskou funkci `type_info::before`. Nezaručujeme, že `type_info::before` vrátí stejný výsledek v různých programech nebo dokonce i v různých spuštěních stejného programu. Tímto způsobem je `type_info::before` podobný operátoru adresy `(&)`.

Členská funkce `type_info::name` vrátí `const char*` na řetězec zakončený hodnotou null, který představuje uživatelsky čitelný název typu. Paměť, na kterou je odkazováno, je uložena do mezipaměti a neměla by nikdy být odebrána přímo.

Členská funkce `type_info::raw_name` vrátí `const char*` na řetězec zakončený hodnotou null, který představuje dekorované jméno typu objektu. Ve skutečnosti je název pro úsporu místa uložen v upravené podobě. V důsledku toho je tato funkce rychlejší než `type_info::name`, protože není nutné rozpracovat název. Řetězec vrácený funkcí `type_info::raw_name` je užitečný při porovnávání operací, ale není čitelný. Pokud potřebujete řetězec čitelný lidmi, použijte místo toho funkci `type_info::name`.

Informace o typu jsou generovány pro polymorfní třídy pouze v případě, že je zadána možnost kompilátoru [/gr (povolit informace běhového typu)](../build/reference/gr-enable-run-time-type-information.md) .

## <a name="see-also"></a>Viz také

[Informace o typu modulu runtime](../cpp/run-time-type-information.md)
