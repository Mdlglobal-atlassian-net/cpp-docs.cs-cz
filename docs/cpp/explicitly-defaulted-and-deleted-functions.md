---
title: Explicitně uvedena a odstranit funkce | Microsoft Docs
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
ms.openlocfilehash: 1f8558a2fac4995d89d0745917e6e1be5ad99d56
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>Explicitně přednastavené a odstraněné funkce
V C ++ 11 přednastavené a odstraněné funkce získáte explicitní kontrolu nad jestli jsou speciální členské funkce automaticky generovány. Odstraněné funkce také poskytují jednoduché jazyk, který chcete zakázat problematické typu povýšení z, ke kterým došlo v argumenty funkce všech typů – speciální členské funkce a také normální členských funkcí a funkcí třetí – které by jinak způsobily volání funkce nežádoucí.  
  
## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>Výhody explicitně uvedena a odstranit funkce  
 V jazyce C++ kompilátor automaticky vygeneruje výchozí konstruktor, kopírovacího konstruktoru, operátor přiřazení kopírování a destruktor pro typ pokud ho nedeklaruje vlastní. Tyto funkce se označují jako *speciální členské funkce*, a jsou co zkontrolujte jednoduché uživatelem definované typy v jazyce C++ chovat jako struktury provést v C. To znamená můžete vytvořit, kopírovat a ničit bez žádné další úsilí kódování. C ++ 11 přináší přesunutí sémantiku jazyk a přidá do seznamu speciální členské funkce, které může automaticky generovat kompilátor konstruktor move a operátor move přiřazení.  
  
 To je vhodné pro jednoduché typy, ale komplexní typy často zadejte nejméně jeden speciální členské funkce sami a to může zabránit jiné speciální členské funkce generován automaticky. V praxi:  
  
-   Pokud žádné konstruktor explicitně deklarována, neexistoval výchozí konstruktor automaticky generovány.  
  
-   Pokud virtuální destruktor explicitně deklarována, žádné výchozí destruktor automaticky generovány.  
  
-   Pokud konstruktor move nebo operátor move přiřazení explicitně deklarována, pak:  
  
    -   Žádné kopírovací konstruktor se automaticky vygeneroval.  
  
    -   Žádné operátor přiřazení kopírování se automaticky vygeneroval.  
  
-   Pokud konstruktor copy, operátor přiřazení kopírovat, přesunout konstruktoru, operátor move přiřazení nebo destruktor explicitně deklarována, pak:  
  
    -   Žádný konstruktor move se automaticky vygeneroval.  
  
    -   Žádné operátor move přiřazení se automaticky vygeneroval.  
  
> [!NOTE]
>  Kromě toho C ++ 11 standardní určuje následující další pravidla:  
>   
>  -   Pokud kopírovacího konstruktoru nebo destruktor explicitně deklarována, automatické generování operátor přiřazení kopie je zastaralý.  
> -   Pokud operátor přiřazení kopírování nebo destruktor explicitně deklarované, pak automatické generování kopírovací konstruktor je zastaralý.  
>   
>  V obou případech Visual Studio nadále automaticky generovat nezbytné funkce implicitně a není posílat upozornění.  
  
 Důsledky tato pravidla můžete taky úniku do objektu hierarchií. Například, pokud z nějakého důvodu nepodaří mít výchozí konstruktor, který lze volat z odvozující třídě základní třídu – to znamená, `public` nebo `protected` konstruktor, které nepřijímá žádné parametry – pak nelze automaticky generovat třídu odvozenou z něj. vlastní výchozí konstruktor.  
  
 Tato pravidla může zkomplikovat implementace co by měl být jednoduché, uživatelem definované typy a běžné idioms C++ – například vytváření uživatelsky definovaný typ. bez kopírovatelná deklarováním kopírovacího konstruktoru a operátor přiřazení kopie soukromě a ne definování je.  
  
```  
struct noncopyable  
{  
  noncopyable() {};  
  
private:  
  noncopyable(const noncopyable&);  
  noncopyable& operator=(const noncopyable&);  
};  
```  
  
 Před C ++ 11 byl tento fragment kódu idiomatickou formu-kopírovatelná typy. Má však několik problémů:  
  
-   Konstruktor copy je třeba deklarovat soukromě ho Pokud chcete skrýt, ale protože je deklarovaná vůbec, automatické generování výchozí konstruktor je nebylo možné provést. Je nutné explicitně definovat výchozí konstruktor, chcete-li, i v případě, že ho neprovede žádnou akci.  
  
-   I když explicitně definován výchozí konstruktor neprovede žádnou akci, považuje netriviální kompilátorem. Je míň efektivní než automaticky generovaný výchozí konstruktor a brání `noncopyable` nebudou typu POD hodnotu true.  
  
-   I když kopírovacího konstruktoru a operátor přiřazení kopie jsou skryta mimo kód, členské funkce a přátelích `noncopyable` stále můžete zobrazit a volat. Pokud jsou deklarovat, ale není definována, volání je způsobí chybu linkeru.  
  
-   Přestože je toto běžně přijatý stylu, záměr není jasné, pokud nerozumíte všechna pravidla pro automatické generování speciální členské funkce.  
  
 Ve C ++ 11 se dají implementovat způsobem, který je více přehledné-kopírovatelná stylu.  
  
```  
struct noncopyable  
{  
  noncopyable() =default;  
  noncopyable(const noncopyable&) =delete;  
  noncopyable& operator=(const noncopyable&) =delete;  
};  
```  
  
 Všimněte si jak problémy s předkonfigurovaného-C ++ 11 stylu jsou vyřešeny:  
  
-   Generování výchozí konstruktor stále brání deklarace konstruktor copy, ale jeho přepnete zpět pomocí explicitně jako výchozí bude použit ho.  
  
-   Explicitně uvedena speciální členské funkce jsou stále považovány za trivial, takže není žádné snížení výkonu a `noncopyable` není zabráněno true POD typu.  
  
-   Kopírovací konstruktor a operátor přiřazení kopie jsou veřejné, ale odstraněný. Jedná o chybu kompilace definovat nebo volání funkce odstraněné.  
  
-   Je třeba vymazat na každý, kdo jste srozuměni s tím `=default` a `=delete`. Nemáte porozumět pravidla pro automatické generování speciální členské funkce.  
  
 Podobně jako idioms existovat pro provedení uživatelem definované typy, které jsou nemobilní, který lze pouze dynamicky přidělit nebo, nelze dynamicky přidělit. Každý z těchto idioms mít pre-C ++ 11 implementace dochází k podobné problémy, a které jsou podobně přeložit v C ++ 11 implementací je z hlediska uvedena a odstranit speciální členské funkce.  
  
## <a name="explicitly-defaulted-functions"></a>Explicitně uvedena funkce  
 Použít výchozí žádné speciální členské funkce – do explicitně stavu, že speciální členské funkce používá výchozí implementace definovat speciální členské funkce se kvalifikátor veřejný přístup, nebo obnovit vyřazenou aplikaci speciální členské funkce, jehož Automatické generování zabránily jiných okolností.  
  
 Speciální členské funkce můžete výchozí deklarováním jako v následujícím příkladu:  
  
```  
struct widget  
{  
  widget()=default;  
  
  inline widget& operator=(const widget&);  
};  
  
inline widget& widget::operator=(const widget&) =default;  
```  
  
 Všimněte si, že, dokud je inlinable použít výchozí speciální členské funkce mimo tělo třídy.  
  
 Z důvodu výhod trivial speciální členské funkce výkonu doporučujeme raději automaticky generované speciální členské funkce nad prázdný funkce subjekty, pokud chcete výchozí chování. Můžete to udělat buď pomocí explicitně jako výchozí bude použit speciální členské funkce, nebo není deklarován (a také není deklarace jiné speciální členské funkce, které by jinak znemožňovaly z generován automaticky.)  
  
## <a name="deleted-functions"></a>Odstraněné funkce  
 Speciální členské funkce a také normální členských funkcí a třetí funkcí, aby s nimi definované nebo názvem můžete odstranit. Odstraňování z speciální členské funkce poskytuje čisticí způsob kompilátor brání v generování speciální členské funkce, které nechcete použít. Funkce musíte odstranit, protože je deklarovaná; nelze jej odstranit později způsobem, můžete funkci deklarovaný a poté převezme později.  
  
```  
struct widget  
{  
  // deleted operator new prevents widget from being dynamically allocated.  
  void* operator new(std::size_t) = delete;  
};  
```  
  
 Odstraňování normální – členská funkce nebo třetí funkce zabraňuje problematické typu povýšení působit nezamýšleným funkce k volání. Toto funguje, protože odstraněné funkce stále účastnit rozlišení přetížení a poskytují lepší shodu než funkce, která může být volána po povýšené typy. Volání funkce přeloží na další specifické – ale odstraněné – funkce a dojde k chybě kompilátoru.  
  
```  
// deleted overload prevents call through type promotion of float to double from succeeding.  
void call_with_true_double_only(float) =delete;  
void call_with_true_double_only(double param) { return; }  
```  
  
 Všimněte si v předchozím příkladu, že volání `call_with_true_double_only` pomocí `float` argument by způsobilo chybu kompilátoru ale volání `call_with_true_double_only` pomocí `int` argument by není; v `int` případě argument bude nastaven z `int` k `double` a úspěšně volat `double` verze funkce, i když, nemusí být co je určená. Aby se zajistilo, že všechny volání této funkce pomocí jiných dvojitou argument způsobí chybu kompilátoru, můžou deklarovat verzi šablony funkce, která se odstraní.  
  
```  
template < typename T >  
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.  
  
void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.  
  
```