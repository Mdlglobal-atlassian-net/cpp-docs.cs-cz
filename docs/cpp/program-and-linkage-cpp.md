---
title: Programy a propojení (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ef0f08efbcdf09420d53710a3f16326381f13c3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056778"
---
# <a name="program-and-linkage-c"></a>Program a propojení (C++)

V programu v jazyce C++ *symbol*, třeba název proměnné nebo funkce, lze deklarovat libovolný počet v rámci svého oboru, ale to je možné definovat jenom jednou. Toto je jedna definice pravidla (ODR). A *deklarace* zavádí (nebo znovu zavádí) název do programu. A *definice* zavádí název a v případě proměnnou, explicitně inicializuje ji. A *funkce definice* se skládá z podpisu plus tělo funkce.

Jde o deklarace:

```cpp
int i;
int f(int x);
```

Následují definice:

```cpp
int i{42};
int f(int x){ return x * i; }
```

Program se skládá z jednoho nebo více *jednotkách překladu*. Jednotky překladu se skládá z implementační soubor (.cpp, .cxx atd.) a všechny hlavičky (.h, .hpp atd.), který zahrnuje přímo nebo nepřímo. Každou jednotku převodu je nezávisle na sobě zkompilovány kompilátorem, po jejímž uplynutí sloučí propojovací program zkompilovaný jednotkami do jednoho *program*. Porušení pravidla ODR obvykle zobrazí jako chyby linkeru Pokud stejný název má dva různé definice v různých jednotkách překladu.

Obecně platí, je nejlepší způsob, jak byla proměnná viditelná napříč více souborů a vložit ho do souboru hlaviček přidejte #include – direktiva v každém souboru .cpp, který vyžaduje deklaraci. Přidáním *zahrnují chrání* kolem obsah těchto hlaviček zajistíte, že názvy deklaruje se definovat pouze jednou.

Nicméně v některých případech může být potřeba deklarovat globální proměnnou nebo třída v souboru s příponou .cpp. V takových případech budete potřebovat způsob, jak zjistit kompilátoru a linkeru, určuje, zda název objektu platí pouze pro jeden soubor, nebo všechny soubory.

## <a name="linkage-vs-scope"></a>Propojení a oboru

Koncept *propojení* označuje, zda globální symboly (například, názvy typů názvy proměnných a funkcí) v rámci programu jako celek mezi jednotkami překladu. Koncept *oboru* odkazuje na symboly, které jsou deklarovány v rámci bloku, jako je například obor názvů, třídy nebo tělo funkce. Tyto značky jsou viditelné pouze v rámci oboru, ve kterém jsou definovány; Koncept propojení se nevztahuje na ně.

## <a name="external-vs-internal-linkage"></a>Vnější vs. vnitřní propojení

A *bezplatná funkce* je funkce, která je definována na globální nebo obor názvů. Non-const globální proměnné a funkce bezplatné ve výchozím nastavení mají *vnější propojení*; jsou viditelné v libovolné jednotce překladu programu. Proto může mít žádné jiné globální objekt (proměnnou, definice třídy atd.) tento název. Symbol s *vnitřní propojení* nebo *bez propojení* je viditelná pouze v rámci jednotce překladu, ve kterém je deklarována. Při název má vnitřní propojení, může se stejným názvem existuje v jiné jednotce překladu. Proměnné deklarované s definicí třídy nebo funkce úřadů, které nemají žádné propojení.

Můžete vynutit na globální název pomocí explicitní deklarace to jako mít interní vazbu **statické**. Tím se omezí jeho viditelnost na stejné jednotce překladu, ve kterém je deklarována. Všimněte si, že v tomto kontextu **statické** znamená něco jiného než při použít pro lokální proměnné.

Následující objekty mít interní vazbu. ve výchozím nastavení:
- objekty konstant
- objekty constexpr.
- definice Typedef
- statické objekty v oboru názvů

Pokud chcete dát konstantní objekt vnější propojení, deklarujte ho jako **extern** a přiřaďte mu hodnotu:

```cpp
extern const int value = 42;
```

Zobrazit [extern](extern-cpp.md) Další informace.

## <a name="see-also"></a>Viz také:

[Základní koncepty](../cpp/basic-concepts-cpp.md)