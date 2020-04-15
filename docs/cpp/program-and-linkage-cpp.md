---
title: Překladové jednotky a propojení (C++)
ms.date: 12/11/2019
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
ms.openlocfilehash: 791ec53d4df863b218db463f2b9b9401bf6f466d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374320"
---
# <a name="translation-units-and-linkage"></a>Jednotky překladu a propojení

V programu jazyka C++ může být *symbol*, například název proměnné nebo funkce, deklarován libovolný počet opakování v rámci jeho oboru, ale lze jej definovat pouze jednou. Toto pravidlo je "Pravidlo jedné definice" (ODR). *Deklarace* zavádí (nebo znovu zavádí) název do programu. *Definice* zavádí název. Pokud název představuje proměnnou, definice ji explicitně inicializuje. *Definice funkce* se skládá z podpisu a těla funkce. Definice třídy se skládá z názvu třídy následované blokem, který obsahuje seznam všech členů třídy. (Těla členských funkcí mohou být volitelně definována samostatně v jiném souboru.)

Následující příklad ukazuje některé deklarace:

```cpp
int i;
int f(int x);
class C;
```

Následující příklad ukazuje některé definice:

```cpp
int i{42};
int f(int x){ return x * i; }
class C {
public:
   void DoSomething();
};
```

Program se skládá z jedné nebo více *překladatelských jednotek*. Jednotka překladu se skládá ze souboru implementace a všech záhlaví, které obsahuje přímo nebo nepřímo. Implementační soubory mají obvykle příponu *cpp* nebo *cxx*. Hlavičkové soubory mají obvykle rozšíření *h* nebo *hpp*. Každá jednotka překladu je kompilována nezávisle kompilátorem. Po dokončení kompilace propojovací program sloučí kompilované jednotky překladu do jednoho *programu*. Porušení pravidla řešení ODR se obvykle zobrazí jako chyby propojovacího zařízení. Linker chyby dojít, pokud stejný název má dvě různé definice v různých jednotkách překladu.

Obecně platí, že nejlepší způsob, jak zviditelnit proměnnou ve více souborech, je vložit ji do souboru záhlaví. Potom přidejte direktivu #include do každého souboru *cpp,* který vyžaduje deklaraci. Přidáním *zahrnout stráže* kolem obsahu záhlaví, zajistíte, že názvy deklaruje jsou definovány pouze jednou.

V jazyce C++20 jsou [moduly](modules-cpp.md) zavedeny jako vylepšená alternativa k souborům hlaviček.

V některých případech může být nutné deklarovat globální proměnnou nebo třídu v souboru *cpp.* V těchto případech potřebujete způsob, jak sdělit kompilátoru a propojovacího serveru, jaký druh *propojení* název má. Typ propojení určuje, zda se název objektu vztahuje pouze na jeden soubor nebo na všechny soubory. Koncept propojení se vztahuje pouze na globální názvy. Koncept propojení se nevztahuje na názvy, které jsou deklarovány v rámci oboru. Obor je určen sadou ohraničujících složených závorek, například v definicích funkcí nebo tříd.

## <a name="external-vs-internal-linkage"></a>Externí vs. vnitřní propojení

Volná *funkce* je funkce, která je definována v globálním oboru nebo oboru oboru názvů. Nekonstovací globální proměnné a volné funkce ve výchozím nastavení mají *externí propojení*; jsou viditelné z libovolné jednotky překladu v programu. Proto žádný jiný globální objekt může mít tento název. Symbol s *vnitřním propojením* nebo *bez propojení* je viditelný pouze v rámci jednotky překladu, ve které je deklarován. Pokud má název vnitřní propojení, stejný název může existovat v jiné jednotce překladu. Proměnné deklarované s definicemi tříd nebo těla funkce nemají žádné propojení.

Globální název můžete vynutit, aby měl interní propojení, explicitním deklarováním jako **statického**. To omezuje jeho viditelnost na stejnou jednotku překladu, ve které je deklarována. V tomto kontextu **statické** znamená něco jiného, než při použití na místní proměnné.

Následující objekty mají ve výchozím nastavení vnitřní propojení:

- const objekty
- objekty constexpr
- definice Typedef
- statické objekty v oboru oboru názvů

Chcete-li dát objektconst externí propojení, deklarovat jako **extern** a přiřadit hodnotu:

```cpp
extern const int value = 42;
```

Další informace naleznete [v extern.](extern-cpp.md)

## <a name="see-also"></a>Viz také

[Základní pojmy](../cpp/basic-concepts-cpp.md)
