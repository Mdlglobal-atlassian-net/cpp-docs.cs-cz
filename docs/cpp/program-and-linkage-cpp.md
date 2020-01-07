---
title: Jednotky překladu a propojení (C++)
ms.date: 12/11/2019
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
ms.openlocfilehash: dcd66b454da3758996fe827581fe4a73a641407f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301350"
---
# <a name="translation-units-and-linkage"></a>Jednotky překladu a propojení

V C++ programu může být *symbol*, například název proměnné nebo funkce, deklarován v rámci oboru libovolným počtem výskytů, ale může být definován pouze jednou. Toto pravidlo je pravidlo "jedno definice" (ODR). *Deklarace* zavádí (nebo znovu zavádí) název do programu. *Definice* zavádí název. Pokud název představuje proměnnou, definice ji explicitně inicializuje. *Definice funkce* se skládá z podpisu a textu funkce. Definice třídy se skládá z názvu třídy následovaného blokem, který obsahuje seznam všech členů třídy. (Subjekty členských funkcí mohou být volitelně definovány samostatně v jiném souboru.)

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

Program se skládá z jedné nebo více *jednotek překladu*. Jednotka překladu se skládá z implementačního souboru a všech hlaviček, které obsahuje přímo nebo nepřímo. Implementační soubory mají obvykle příponu souboru *cpp* nebo *příponu CXX*. Hlavičkové soubory mají obvykle příponu *h* nebo *HPP*. Jednotlivé jednotky překladu jsou kompilovány nezávisle na kompilátoru. Po dokončení kompilace linker sloučí zkompilované jednotky překladu do jednoho *programu*. Porušení pravidla ODR se obvykle zobrazují jako chyby linkeru. K chybám linkeru dochází, když má stejný název dvě různé definice v různých jednotkách překladu.

Obecně je nejlepší způsob, jak nastavit proměnnou jako viditelnou v rámci více souborů, je umístit do hlavičkového souboru. Pak přidejte direktivu #include do každého souboru *cpp* , který vyžaduje deklaraci. Přidáním *ochranných krytí* pro obsah záhlaví zajistíte, že názvy, které deklaruje, budou definovány pouze jednou.

V C++ 20 jsou [moduly](modules-cpp.md) představeny jako Vylepšená alternativa k hlavičkovým souborům.

V některých případech může být nutné deklarovat globální proměnnou nebo třídu v souboru *cpp* . V těchto případech potřebujete způsob, jak říct kompilátoru a linkeru, jaký typ *propojení* má název. Typ propojení určuje, zda se název objektu vztahuje pouze na jeden soubor nebo na všechny soubory. Pojem propojení se vztahuje pouze na globální názvy. Koncept propojení se nevztahuje na názvy, které jsou deklarovány v rámci oboru. Obor je určen sadou ohraničujících složených závorek, například v definicích funkce nebo třídy.

## <a name="external-vs-internal-linkage"></a>Externí a interní propojení

*Bezplatná funkce* je funkce, která je definována v oboru názvů Global nebo Namespace. Nekonstantní globální proměnné a bezplatné funkce ve výchozím nastavení mají *vnější propojení*; jsou viditelné z jakékoli jednotky překladu v programu. Proto žádný jiný globální objekt nemůže mít tento název. Symbol s *vnitřním propojením* nebo *bez propojení* je viditelný pouze v rámci jednotky překladu, ve které je deklarována. Pokud má název vnitřní propojení, může stejný název existovat v jiné jednotce překladu. Proměnné deklarované s definicemi třídy nebo texty funkcí nemají žádné propojení.

Můžete vynutit, aby globální název měl interní propojení explicitním deklarováním jako **static**. Tím se omezí jeho viditelnost na stejnou jednotku překladu, v níž je deklarována. V tomto kontextu **statický** znamená něco jiného než při použití na lokální proměnné.

Ve výchozím nastavení mají následující objekty interní propojení:
- objekty const
- objekty constexpr
- definice Typedef
- statické objekty v oboru názvů

Chcete-li přidělit objektu const vnější propojení, deklarujte ho jako **extern** a přiřaďte mu hodnotu:

```cpp
extern const int value = 42;
```

Další informace najdete v tématu [extern](extern-cpp.md) .

## <a name="see-also"></a>Viz také:

[Základní koncepty](../cpp/basic-concepts-cpp.md)