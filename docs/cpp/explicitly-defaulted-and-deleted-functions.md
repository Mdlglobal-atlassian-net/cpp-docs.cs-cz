---
title: Explicitně nastavených a odstraněných funkcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69058c00757cea466683246c1aee2e89f806c931
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058604"
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>Explicitně přednastavené a odstraněné funkce

V C ++ 11 přednastavené a odstraněné funkce poskytují explicitní kontrolu nad Určuje, zda jsou automaticky generovány zvláštní členské funkce. Odstraněné funkce také poskytují jednoduchý jazyk pro zabránění problematického typu propagací z, ke kterým došlo v argumentech funkcí všechny typy – zvláštní členské funkce stejně jako normální členské funkce a nečlenské funkce, které by mohly jinak způsobit volání nežádoucí funkce.

## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>Výhody explicitně nastavených a odstraněných funkcí

V jazyce C++ kompilátor automaticky generuje výchozí konstruktor, konstruktor kopie, operátor přiřazení kopie a destruktor pro typ Pokud nedeklaruje svou vlastní. Tyto funkce jsou označovány jako *speciálních členských funkcí*, a nim se jednoduché typy definované uživatelem v jazyce C++ chovají jako struktury v jazyce C. To znamená můžete vytvořit, kopírovat a zničit bez jakéhokoli dalšího kódování úsilí. C ++ 11 přináší přesunutí sémantiky jazyka a přidá do seznamu speciálních členských funkcí, které může kompilátor automaticky generovat konstruktor move a operátor přiřazení přesunu.

Tato možnost je pohodlná pro jednoduché typy, ale komplexní typy často definují jednu nebo více speciálních členských funkcí, sami a to může zabránit zabránily automatickému generování dalších zvláštních členských funkcí. V praxi:

- Pokud je některý konstruktor explicitně deklarovány, pak žádný výchozí konstruktor není automaticky vygenerován.

- Pokud jsou virtuální destruktor výslovně deklarovány, pak žádný výchozí destruktor není automaticky vygenerován.

- Pokud konstruktor move a operátor přiřazení přesunu výslovně deklarovány, pak:

   - Žádný konstruktor kopie není automaticky vygenerován.

   - Žádný operátor přiřazení kopie není automaticky vygenerován.

- Pokud kopírovacího konstruktoru, operátor přiřazení kopie, přesunutí konstruktoru, operátor přiřazení přesunu nebo destruktor výslovně deklarovány, pak:

   - Žádný konstruktor přesunu není automaticky vygenerován.

   - Žádný operátor přiřazení přesunu není automaticky vygenerován.

> [!NOTE]
>  Kromě toho standardu C ++ 11 určuje následující další pravidla:
>
>  -   Pokud je kopírovací konstruktor nebo destruktor výslovně deklarovány, automatické generování operátor přiřazení kopie je zastaralý.
> -   Pokud operátor přiřazení kopie nebo destruktor je explicitně deklarované, pak automatické generování kopírovací konstruktor je zastaralý.
>
>  V obou případech se Visual Studio nadále automaticky generovat nezbytné funkce implicitně a negeneruje upozornění.

Důsledky tato pravidla mohou také způsobit únik těchto do hierarchie objektů. Například, pokud z nějakého důvodu nepodaří mít výchozí konstruktor, který lze volat z odvozená třída základní třídy – to znamená, **veřejné** nebo **chráněné** konstruktor, který nepřijímá žádné parametry – potom třídy která je odvozena od nemůže automaticky generovat vlastní výchozí konstruktor.

Tato pravidla mohou zkomplikovat implementaci toho, co by měl být přímočaré, uživatelem definované typy a společné idiomy v jazyce C++ – například vytvoření uživatelem definovaného typu nekopírovatelných deklarováním konstruktoru kopie a operátor přiřazení kopie soukromě a nikoli jejich definováním.

```cpp
struct noncopyable
{
  noncopyable() {};

private:
  noncopyable(const noncopyable&);
  noncopyable& operator=(const noncopyable&);
};
```

Před C ++ 11 byl tento fragment kódu idiomatickou formou nekopírovatelných typů. Má však několik problémů:

- Kopírovací konstruktor musí deklarovat soukromě a tak jej skrýt, ale protože vůbec je deklarován, automatickému generování výchozího konstruktoru je zabráněno. Je nutné explicitně definovat výchozí konstruktor, chcete-li, i když to nemá žádný účinek.

- I v případě, že explicitně definovaný výchozí konstruktor neprovede žádnou akci, bude považován za netriviální kompilátorem. Je méně efektivní než automaticky generovaný výchozí konstruktor a brání `noncopyable` z POD typem.

- Přestože konstruktor kopie a operátor přiřazení kopie jsou skryty z vnějšího kódu, členské funkce a přáteli `noncopyable` můžete stále vidět a jejich volání. Pokud jsou deklarovány, ale nejsou definovány, jejich volání způsobí chybu linkeru.

- I když se jedná o obecně uznávaný idiom, záměr není jasný, pokud neznáte všechna pravidla pro automatické generování speciálních členských funkcí.

V C ++ 11 je možné implementovat nekopírovatelných idiom způsobem, který je přímější.

```cpp
struct noncopyable
{
  noncopyable() =default;
  noncopyable(const noncopyable&) =delete;
  noncopyable& operator=(const noncopyable&) =delete;
};
```

Všimněte si, že jak problémy s předdefinovanou-C ++ 11 idiomu:

- Generování výchozího konstruktoru je stále bráněno deklarací kopírovacího konstruktoru, ale můžete ho přenést zpět jeho explicitním přednastavením ho.

- Explicitně výchozích speciálních členských funkcí jsou stále považovány za bezvýznamné, takže není k dispozici žádné snížení výkonu a `noncopyable` není zabráněno typem POD.

- Konstruktor kopie a operátor přiřazení kopie jsou veřejné, ale byl odstraněn. Je chyba kompilace pro definování nebo volání odstraněné funkce.

- Záměr je jasný každému, kdo rozumí `=default` a `=delete`. Nemusíte pochopit pravidla pro automatické generování speciálních členských funkcí.

Podobné idiomy existují pro vytvoření uživatelem definovaných typů, které jsou nepohyblivé, který může být pouze dynamicky přiřazovány nebo, který nejde dynamicky přidělit. Každá z těchto idiomy mít pre-předimplementace C ++ 11, které trpí podobnými problémy a které jsou podobně řešeny v C ++ 11 jejich implementací výchozích a odstraněných speciálních členských funkcí.

## <a name="explicitly-defaulted-functions"></a>Explicitně nastavena výchozí hodnota funkce

Použít výchozí jakékoli zvláštní členské funkce – k výslovnému, že zvláštní členská funkce používá výchozí implementace k definování zvláštní členskou funkci s kvalifikátorem veřejného přístupu nebo obnovit zvláštní členské funkce, jehož Automatické generování nedošlo z důvodu jiné okolnosti.

Výchozí funkce zvláštních členských deklarováním jako v následujícím příkladu:

```cpp
struct widget
{
  widget()=default;

  inline widget& operator=(const widget&);
};

inline widget& widget::operator=(const widget&) =default;
```

Všimněte si, že použít výchozí zvláštní členské funkce mimo tělo třídy za předpokladu, že jsou vložitelné.

Protože výkony těží z triviálních zvláštních členských funkcí doporučujeme raději automaticky generovat zvláštní členské funkce nad prázdnými funkcemi, pokud chcete výchozí chování. Můžete to provést jeho explicitním přednastavením speciální členská funkce nebo nedeklarováním (a také nedeklarováním dalších speciálních členských funkcí, které by zabránily automatickému generování.)

## <a name="deleted-functions"></a>Odstraněné funkce

Můžete odstranit speciální členské funkce stejně jako normální členské funkce a nečlenské funkce, chcete-li zabránit tak jejich definování nebo volání. Odstranění zvláštních členských funkcí umožňuje čistší způsob zabránění kompilátoru generovat speciálních členské funkce, které nechcete. Funkce musí odstranit, protože je deklarován; nelze jej odstranit později ve způsobu, jakým může funkce deklarované a pak později nastavit na výchozí hodnotu.

```cpp
struct widget
{
  // deleted operator new prevents widget from being dynamically allocated.
  void* operator new(std::size_t) = delete;
};
```

Odstraňování běžné členské funkce a nečlenské funkce zabraňuje problematickým způsobily nežádoucích funkcí k volání. Tento postup funguje, protože odstraněné funkce se stále účastní řešení přetížení a poskytnutí lepší shody než funkce, která lze volat po propagaci typů. Volání funkce se překládá na konkrétní informace, ale odstraněné – funkce a způsobí chybu kompilátoru.

```cpp
// deleted overload prevents call through type promotion of float to double from succeeding.
void call_with_true_double_only(float) =delete;
void call_with_true_double_only(double param) { return; }
```

V předchozím příkladu si všimněte, že volání `call_with_true_double_only` pomocí **float** argumentu by způsobila chybu kompilátoru, ale volání `call_with_true_double_only` pomocí **int** by argument; v **int** případech argumentem budou přesunuty z **int** k **double** a úspěšně volat **double** verzi funkce, i když, která nemusí být, co je určen. Aby bylo zajištěno, že jakékoli volání této funkce použitím nezdvojeného argumentu způsobí chybu kompilátoru, můžete deklarovat verzi šablony funkce, která se odstraní.

```cpp
template < typename T >
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.

void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.
```