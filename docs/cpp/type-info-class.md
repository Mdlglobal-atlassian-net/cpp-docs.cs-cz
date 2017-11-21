---
title: "type_info – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_info
dev_langs: C++
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 61e26b60916712e10c1c0fa5b255aa7bf2bc1fd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="typeinfo-class"></a>type_info – třída
**Type_info** třída popisuje informace o typu generované v rámci programu kompilátoru. Objekty této třídy účinně ukládají ukazatel na název typu. **Type_info** třída také ukládá hodnotu kódovaného vhodný pro porovnání rovnosti dvou typů nebo pořadí řazení. Pravidla kódování a pořadí řazení typů nejsou specifikována a mezi programy se mohou lišit.  
  
 `<typeinfo>` Musí být součástí, aby bylo možné používat hlavičkový soubor **type_info** třídy. Rozhraní pro **type_info** třída je:  
  
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
  
 Nelze doložit objekty **type_info** třídy přímo, protože třída má pouze privátní kopírovacího konstruktoru. Jediný způsob, jak vytvořit (dočasný) **type_info** objekt, je použít [typeid](../cpp/typeid-operator.md) operátor. Vzhledem k tomu, že je operátor přiřazení také privátní, nelze kopírovat nebo přiřazovat objekty třídy **type_info**.  
  
 **type_info::hash_code** definuje vhodný pro mapování hodnoty typu funkce hash **TypeInfo –** k distribučnímu index hodnot.  
  
 Operátory `==` a `!=` lze použít k porovnání rovnosti a nerovnosti s jinými **type_info** objekty, v uvedeném pořadí.  
  
 Neexistuje žádná souvislost mezi pořadím řazení typů a vztahy dědičnosti. Použití **type_info::before** – členská funkce k určení pořadí řazení typů. Neexistuje žádná záruka, **type_info::before** předá stejný výsledek v různých aplikacích nebo i jiné spustí stejný program. Tímto způsobem **type_info::before** je podobná adresu z **(&)** operátor.  
  
 **Type_info::name** – členská funkce vrátí **const char\***  představující čitelný název typu do řetězce ukončené hodnotou null. Paměť, na kterou je odkazováno, je uložena do mezipaměti a neměla by nikdy být odebrána přímo.  
  
 **Type_info::raw_name** – členská funkce vrátí **const char\***  představující upravený název typu objektu do řetězce ukončené hodnotou null. Ve skutečnosti je název pro úsporu místa uložen v upravené podobě. V důsledku toho se tato funkce je rychlejší než **type_info::name** protože nepotřebuje odstaranit úpravy názvu. Řetězec vrácený **type_info::raw_name** funkce je užitečná v operace porovnání, ale není možné číst. Pokud potřebujete čitelná pro člověka řetězec, použijte **type_info::name** funkce místo.  
  
 Typ informace se generují pro polymorfní třídy pouze v případě [/GR (Povolit Run-Time informace typu)](../build/reference/gr-enable-run-time-type-information.md) – možnost kompilátoru je zadán.  
  
## <a name="see-also"></a>Viz také  
 [Informace běhového typu](../cpp/run-time-type-information.md)
