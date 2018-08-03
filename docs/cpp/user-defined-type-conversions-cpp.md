---
title: Uživatelem definované převody typu (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- explicit_cpp
dev_langs:
- C++
helpviewer_keywords:
- constructors [C++], and constants
- conversion functions [C++]
- explicit keyword [C++]
- type conversion
- constructors [C++], drawbacks
- conversion constructors
- type conversion [C++], explicit conversion
- coercion [C++]
- conversions [C++], explicit
- objects [C++], converting
- conversion functions [C++], rules for declaring
- declaring functions [C++], conversion functions
- functions [C++], conversion
- converting objects
- constructors [C++], conversion
- conversions [C++], by constructors
- data type conversion [C++], explicit
ms.assetid: d40e4310-a190-4e95-a34c-22c5c20aa0b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5040319bee3fa74319bb30ca45ff11f2f5d72720
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465929"
---
# <a name="user-defined-type-conversions-c"></a>Uživatelem definovaný typ převody (C++)
A *převod* vytvoří novou hodnotu typu některé z hodnoty jiného typu. *Standardní převody* jsou integrované do jazyka C++ a podporu jeho předdefinovaných typů, případně můžete vytvořit *uživatelem definované převody* provádět převody na, z nebo mezi uživatelem definované typy.  
  
 Standardní převody provádět převody mezi vestavěné typy, mezi ukazatele nebo odkazy na typy související s děděním do a z ukazatelů typu void a ukazatele s hodnotou null. Další informace najdete v tématu [standardní převody](../cpp/standard-conversions.md). Uživatelem definované převody provádět převody mezi typy definované uživatelem, nebo mezi uživatelem definovaných typů a vestavěné typy. Můžete implementovat jako [konstruktory převodu](#ConvCTOR) nebo jako [funkce pro převod](#ConvFunc).  
  
 Převod může být buď explicitní – když volá programátora pro jeden typ má být převeden na jiný, stejně jako v přetypování nebo přímou inicializací – nebo implicitní – když jazyk nebo program volá pro jiný typ než ten, který programátorem.  
  
 Nedochází k pokusům o implicitních převodů při:  
  
-   Argument zadaný pro funkce nemá stejný typ jako odpovídající parametr.  
  
-   Hodnota vrácená z funkce nemá stejný typ jako návratový typ funkce.  
  
-   Inicializační výraz nemá stejný typ jako objekt, který je inicializace.  
  
-   Výraz, který řídí podmíněném příkazu, uvozuje konstruktor cyklu nebo přepínač nemá typ výsledku, který je potřeba ji řídit.  
  
-   Zadaný operátor operand nemá stejný typ jako odpovídající parametr operand. Integrované operátory oba operandy musí být stejného typu a se převedou na společný typ, který může představovat i. Další informace najdete v tématu [standardní převody](standard-conversions.md). Pro uživatelsky definované operátory každý operand musí být stejného typu jako odpovídající parametr operand.  
  
 Pokud jeden standardní převod nelze provést implicitní převod, kompilátor může použít uživatelsky definovaný převod, volitelně následovaný další standardní převod, k jejímu dokončení.  
  
 Když dva nebo více uživatelem definovaných převodů, které provádějí stejné převodu jsou k dispozici v lokalitě převodu, převod se říká, že byly nejednoznačné. Tyto nejednoznačnosti jsou chybu, protože kompilátor nemůže určit, který z nich k dispozici převodů by měl vybrat. Však není právě k definování více způsoby provedení stejný převod, protože sadu dostupné převody může lišit na různých místech ve zdrojovém kódu k chybě – v závislosti na záhlaví, které například soubory jsou zahrnuty ve zdrojovém souboru. Pouze jeden převod je k dispozici v lokalitě převod, nedochází k nejednoznačnosti. Existuje několik způsobů, které mohou vzniknout nejednoznačné převody, ale ty nejběžnější:  
  
-   Vícenásobná dědičnost. Převod je definován více než jedné základní třídy. 
  
-   Volání funkce nejednoznačné. Převod je definován jako konstruktor převodu cílového typu a funkce pro převod typu zdroje. Další informace najdete v tématu [funkce pro převod](#ConvFunc).  
  
 Obvykle lze vyřešit nejednoznačnost právě ručním kvalifikováním názvu typu zahrnutých podrobněji nebo provedením explicitní přetypování pro upřesnění vašeho záměru.  
  
 Konstruktory převodu a funkce pro převod dodržují pravidla pro řízení přístupu ke členům, ale usnadnění převody považuje pouze pokud se dá určit jednoznačný převod. To znamená, že převod je nejednoznačný i v případě, že úroveň přístupu konkurenční převodu by jinak znemožňovaly z používán. Další informace o usnadnění přístupu člena, naleznete v tématu [řízení přístupu ke členu](../cpp/member-access-control-cpp.md).  
  
## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Explicit – klíčové slovo a problémy s implicitní převod  
 Ve výchozím nastavení při vytvoření uživatelem definovaného převodu, kompilátor může použít ho k provádění implicitních převodů. Někdy to je, co chcete, ale jindy jednoduchých pravidel, které provedou kompilátor při provádění implicitních převodů může způsobit ho tak, aby přijímal kód, který nechcete, aby ji.  
  
 Dobře známé příkladem implicitní převod, který může způsobit potíže, je převod **bool**. Existuje mnoho důvodů, které můžete chtít vytvořit typ třídy, který lze použít v kontextu logické hodnoty – například tak, že je možné do ovládacího prvku **Pokud** příkazu nebo smyčku –, ale když kompilátor provádí uživatelsky definovaný převod do předdefinovaný typ, kompilátor může použít později další standardní převod. Záměr tato další standardní převod je umožnit věci, jako je povýšení z **krátký** k **int**, ale také otevírá dveře méně zřejmé převody – třeba z  **BOOL** k **int**, který umožňuje typ třída se používá v kontextech celé číslo nikdy určené. Tento konkrétní problém se označuje jako *bezpečné Bool problém*. Tento druh problému je tam, kde **explicitní** – klíčové slovo může pomoct.  
  
 **Explicitní** – klíčové slovo sděluje kompilátoru, že zadaný převod nelze použít k provádění implicitních převodů. Pokud jste chtěli syntaktické pohodlí implicitních převodů před **explicitní** – klíčové slovo byl zaveden, musíte přijmout nežádoucí důsledky této implicitní převod někdy vytvořit nebo použít méně vhodné, jako alternativní řešení s názvem funkce pro převod. Nyní, s použitím **explicitní** – klíčové slovo, můžete vytvořit vhodné převodů, který jde použít jenom k provedení explicitního přetypování nebo přímé inicializace a, která nevede k druh problémy příklad problém bezpečného typu Bool.  
  
 **Explicitní** – klíčové slovo lze použít konstruktory převodu od verze C ++ 98 a funkce pro převod od verze C ++ 11. Následující části obsahují další informace o tom, jak používat **explicitní** – klíčové slovo.  
  
## <a name="ConvCTOR"></a> Konstruktory převodu  
 Konstruktory převodu definujte převody z typů definovaný uživatelem nebo předdefinovaný na typ definovaný uživatelem. Následující příklad ukazuje konstruktor převodu, který převede z předdefinovaného typu **double** pro uživatelem definovaný typ `Money`.  
  
```cpp 
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    Money(double _amount) : amount{ _amount } {};  
  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << balance.amount << std::endl;  
}  
  
int main(int argc, char* argv[])  
{  
    Money payable{ 79.99 };  
  
    display_balance(payable);  
    display_balance(49.95);  
    display_balance(9.99f);  
  
    return 0;  
}  
```  
  
 Všimněte si, že první volání funkce `display_balance`, která přebírá argument typu `Money`, nevyžaduje převod, protože její argument je nesprávného typu. Ale v druhé volání `display_balance`, převod je potřeba, protože typ argumentu, **double** s hodnotou `49.95`, není co funkce očekává. Funkci nelze použít tuto hodnotu přímo, ale protože existuje převod z typu argumentu –**double**– na typ odpovídající parametr –`Money`– dočasná hodnota typu `Money` je vytvořen z argument a použít k dokončení volání funkce. Ve třetím volání `display_balance`, Všimněte si, že argument je **double**, ale místo toho je **float** s hodnotou `9.99`– a ještě volání funkce lze stále dokončit, protože Kompilátor může provádět standardní převod – v takovém případě z **float** k **double**– a pak proveďte uživatelem definovaná konverze z **double** k `Money` pro dokončení převodu nezbytné.  
  
### <a name="declaring-conversion-constructors"></a>Deklarování konstruktory převodu  
 Platí následující pravidla pro deklarování konstruktor převodu:  
  
-   Cílový typ převodu je uživatelem definovaný typ, který se vytváří.  
  
-   Konstruktory převodu obvykle trvat právě jeden argument, který je typem zdroje. Konstruktor převodu však můžete zadat další parametry, pokud každá další parametr má výchozí hodnotu. Typ zdroje zůstávají první parametr typu.  
  
-   Konstruktory převodu, stejně jako všechny konstruktory není zadán typ vrácené hodnoty. Chcete-li se o chybu, určující návratový typ v deklaraci.  
  
-   Konstruktory převodu lze explicitní.  
  
### <a name="explicit-conversion-constructors"></a>Explicitní převod konstruktory  
 Deklarováním konstruktoru převod bude **explicitní**, ho jde použít jenom pro přímé inicializaci objektu nebo provést explicitní přetypování. Díky tomu funkce, které přijímají argument typu třídy také implicitně přijímat argumenty typu konstruktor převodu zdroje a brání typu třídy inicializovat kopírování z hodnoty typu zdroje. Následující příklad ukazuje, jak definovat konstruktor explicitní převod a účinek, který má na jaký kód je ve správném formátu.  
  
```cpp 
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    explicit Money(double _amount) : amount{ _amount } {};  
  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << balance.amount << std::endl;  
}  
  
int main(int argc, char* argv[])  
{  
    Money payable{ 79.99 };        // Legal: direct initialization is explicit.  
  
    display_balance(payable);      // Legal: no conversion required  
    display_balance(49.95);        // Error: no suitable conversion exists to convert from double to Money.  
    display_balance((Money)9.99f); // Legal: explicit cast to Money  
  
    return 0;  
}  
```  
  
 V tomto příkladu, Všimněte si, že můžete použít konstruktor explicitního převodu stále provádět přímé inicializace `payable`. Pokud místo toho byste chtěli kopírování inicializace `Money payable = 79.99;`, bude k chybě. První volání `display_balance` je poškozena, protože argument je nesprávného typu. Druhé volání `display_balance` se o chybu, protože konstruktor převodu nelze použít k provádění implicitních převodů. Třetí volání `display_balance` je platný, protože explicitní přetypování na `Money`, ale Všimněte si, že kompilátor stále povedlo dokončit přetypování vložením implicitní přetypování z **float** k **double**.  
  
 I v pohodlí umožňuje implicitní převod může být lákavé, učiníte tak můžou způsobit obtížné najít chyby. Pravidlem je, aby všechny konstruktory převodu explicitní s výjimkou případů, kdy jste si jisti, který má konkrétní převodu dojde k implicitně.  
  
##  <a name="ConvFunc"></a> Funkce pro převod  
 Funkce pro převod definujte převody z uživatelem definovaného typu na jiné typy. Tyto funkce jsou někdy označovány jako "operátory přetypování", protože, spolu s konstruktory převodu jsou volány při hodnota je přetypována na jiný typ. Následující příklad ukazuje funkce převodu, která převede typ definovaný uživatelem `Money`, na předdefinovaný typ **double**:  
  
```cpp 
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    Money(double _amount) : amount{ _amount } {};  
  
    operator double() const { return amount; }  
private:  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << balance << std::endl;  
}  
```  
  
 Všimněte si, že členské proměnné `amount` tvoří privátní a že veřejné převod funkce na typ **double** se používá jenom k vrácení hodnoty `amount`. Ve funkci `display_balance`, dojde k implicitní převod při hodnotu `balance` streamuje do standardního výstupu pomocí operátor vkládání datového proudu `<<`. Vzhledem k tomu, že je definován žádný operátor vkládání datového proudu pro uživatelem definovaný typ `Money`, ale je jedna pro předdefinovaný typ **double**, kompilátor může použít funkce pro převod z `Money` k **double** splňovat operátor vkládání datového proudu.  
  
 Funkce převodu jsou zděděny z odvozených tříd. Funkce pro převod v odvozené třídě přepsat zděděný konverze funkce pouze při převodu do stejného typu. Například uživatelem definovaný převod funkce odvozené třídy **operator int** nepřepisuje – nebo dokonce vliv – uživatelsky definovaný převod funkce základní třídy **operator short**, dokonce i i když standardní převody definovat převod vztah mezi **int** a **krátký**.  
  
### <a name="declaring-conversion-functions"></a>Deklarace funkcí převodu  
 K deklaraci funkce pro převod platí následující pravidla:  
  
-   Cílový typ převodu musí být deklarována před deklarací funkce pro převod. Třídy, struktury, výčty a definice TypeDef nemůže být deklarována v rámci deklarace funkcí převodu.  
  
    ```cpp 
    operator struct String { char string_storage; }() // illegal  
    ```  
  
-   Funkce převodu nepřijímají argumenty. Zadání parametrů v deklaraci se o chybu.  
  
-   Funkce převodu mají návratový typ, který je zadán název funkce pro převod, který je zároveň názvem převod na typ cíle. Chcete-li se o chybu, určující návratový typ v deklaraci.  
  
-   Funkce pro převod může být virtuální.  
  
-   Funkce pro převod může být explicitní.  
  
### <a name="explicit-conversion-functions"></a>Funkce pro explicitní převod  
 Při převodu funkce je deklarovaná jako explicitní, můžete použít jenom k provádění explicitní přetypování. Díky tomu funkce, které přijímají argument funkce pro převod typu cílového také implicitně přijímat argumenty typu třídy a brání instance cílového typu kopírování inicializována z hodnoty typu třídy. Následující příklad ukazuje, jak definovat funkci explicitního převodu platnosti a účinnosti má na to, jaký kód je ve správném formátu.  
  
```cpp 
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    Money(double _amount) : amount{ _amount } {};  
  
    explicit operator double() const { return amount; }  
private:  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << (double)balance << std::endl;  
}  
```  
  
 Tady funkce pro převod **operátor double** byl proveden explicitní a explicitní přetypování na typ **double** zavedl se ve funkci `display_balance` k provedení převodu. Pokud toto přetypování byly vynechány, kompilátor by nelze najít vhodný stream vložení operátoru `<<` pro typ `Money` a dojde k chybě.  