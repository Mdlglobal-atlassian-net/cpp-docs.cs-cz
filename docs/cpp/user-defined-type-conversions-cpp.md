---
title: "Uživatelem definované převody typů (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 561730527a215d5314f7239affc764d9f5925f67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-type-conversions-c"></a>Typ uživatelem definované převody (C++)
A *převod* vytvoří novou hodnotu typu z hodnoty jiného typu. *Standardní převody* jsou integrované do jazyka C++ a podpora, jeho vestavěné typy, případně můžete vytvořit *uživatelem definované převody* provést převody k, od nebo mezi uživatelem definované typy.  
  
 Standardní převody provést převody mezi vestavěné typy mezi ukazatele nebo odkazy na typy související podle dědičnosti, do a z neplatné ukazatele a na ukazatele null. Další informace najdete v tématu [standardní převody](../cpp/standard-conversions.md). Uživatelem definované převody provést převody mezi uživatelem definované typy nebo mezi uživatelem definovaných typů a vestavěné typy. Můžete implementovat, je jako [konstruktory převodu](#ConvCTOR) nebo jako [funkce pro převod](#ConvFunc).  
  
 Převody může být buď explicitní – když programátorů volá pro jeden typ má být převeden na jiné, jako cast nebo přímé inicializace – nebo implicitní – při volání pro jiného typu než ten, který poskytují programátorů jazyk nebo program.  
  
 Implicitní převody se pokus při:  
  
-   Argument zadaný pro funkci nemá stejný typ jako odpovídající parametr.  
  
-   Hodnota vrácená z funkce nemá stejný typ jako návratový typ funkce.  
  
-   Výraz inicializátoru nemá stejný typ jako objekt, který je inicializace.  
  
-   Výraz, který řídí podmíněného prohlášení, opakování konstrukce nebo přepínač nemá typem výsledku, který je potřeba řídit.  
  
-   Operand zadané operátor nemá stejný typ jako odpovídající operand parametr. Předdefinované operátorů oba operandy musí mít stejný typ a se převedou na společný typ, který může představovat obě. Další informace najdete v tématu [standardní převody](standard-conversions.md). Pro uživatelem definované operátory musí mít každý operand stejného typu jako odpovídající operand parametr.  
  
 Pokud jeden standardní převod nelze dokončit implicitní převod, kompilátor použít uživatelem definovaný převod, následuje další standardní převod, volitelně dokončit, protože se.  
  
 Při dvou nebo více uživatelem definované převody provádějící stejné převod jsou k dispozici v lokalitě převodu, převod se říká, že nejednoznačný. Takové nejednoznačnosti jsou k chybě, protože kompilátor nemůže určit, které jeden z dostupných převody by si měli vybrat. Však není právě k definování více způsobů provádění stejné převodu, protože sada k dispozici převody může lišit v různých umístěních ve zdrojovém kódu chybu – například v závislosti na tom, které hlavičky souborů jsou součástí zdrojového souboru. Tak dlouho, dokud pouze jeden převod je k dispozici v lokalitě převodu, nedochází k nejednoznačnosti. Existuje několik způsobů, které mohou nastat nejednoznačné převody, ale většina běžných ty, které jsou:  
  
-   Vícenásobná dědičnost. Převod je definována v více než jedné základní třídy. 
  
-   Volání funkce nejednoznačný. Převod je definován jako konstruktor převod cílového typu a jako funkci pro převod typu zdroje. Další informace najdete v tématu [funkce pro převod](#ConvFunc).  
  
 Obvykle můžete vyřešit to nejednoznačnost právě kvalifikováním názvu typu zahrnutých podrobněji nebo provedením explicitní přetypování o vysvětlení vašich představ.  
  
 Konstruktory převodu a funkce pro převod orientují pravidly řízení přístupu člena, ale usnadnění převody považuje pouze pokud jednoznačným převod se dá určit. To znamená, že převodu z může být nejednoznačný i v případě, že úroveň přístupu tohoto převodu z konkurenční by zabránit, aby ji používal. Další informace o usnadnění člen najdete v tématu [řízení přístupu ke členu](../cpp/member-access-control-cpp.md).  
  
## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Explicit – klíčové slovo a problémy s implicitní převod  
 Ve výchozím nastavení při vytváření převodu z uživatelem definované kompilátor můžete použít ji k provedení implicitní převody. Někdy je co chcete použít, ale jiné časy jednoduchých pravidel, které průvodce kompilátoru při vytvoření implicitní převody může způsobit pro přijetí kód, který nechcete, aby bylo k.  
  
 Dobře známé příkladem implicitní převod, který může způsobit problémy je převod `bool`. Existuje mnoho důvodů, které můžete chtít vytvořit typu třídy, který lze použít v kontextu, logická hodnota – například, které slouží k řízení `if` příkaz nebo smyčky – ale když kompilátor provede převod uživatelem definované pro předdefinovaný typ , kompilátor může používat další standardní konverzi později. Záměr tento další standardní převod je umožnit pro takové věci, jako povýšení z `short` k `int`, ale také otevře dveře méně zřejmé převody – například z `bool` k `int`, což umožňuje třídě typ, který se má použít v kontextu celé číslo, které nikdy určený. Tento konkrétní problém se označuje jako *bezpečné Bool problém*. Tento druh problému je, kdy `explicit` může pomoci – klíčové slovo.  
  
 `explicit` – Klíčové slovo říká kompilátoru, že zadanou konverzi nelze použít k provedení implicitní převody. Pokud jste chtěli syntaktické pohodlí implicitní převody před `explicit` byla zavedena – klíčové slovo, jste museli přijměte nezamýšleným důsledky tohoto implicitní převod někdy vytvořit nebo použít převod méně praktické, s názvem funkce jako alternativní řešení. Nyní, pomocí `explicit` – klíčové slovo, můžete vytvořit pohodlný převody pouze který lze použít k provedení explicitní přetypování nebo přímé inicializace a který nevede k druh problémy příklad bezpečné Bool problém.  
  
 `explicit` – Klíčové slovo lze použít k konstruktory převodu od C ++ 98 a funkce pro převod od C ++ 11. Následující části obsahují další informace o tom, jak používat `explicit` – klíčové slovo.  
  
##  <a name="ConvCTOR"></a>Konstruktory převodu  
 Konstruktory převodu definujte převody z typů uživatelem definované a integrované typu definovaný uživatelem. Následující příklad ukazuje, převod konstruktor, který převádí z předdefinovaný typ `double` pro uživatelem definovaný typ `Money`.  
  
```  
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
  
 Všimněte si, že první volání funkce `display_balance`, což trvá argument typu `Money`, nevyžaduje převod, protože její argument není správného typu. Ale na druhé volání `display_balance`, převod je potřeba, protože typ argumentu, `double` s hodnotou `49.95`, je, není co funkce očekává. Tuto hodnotu nelze použít přímo, funkce, ale protože je převod z typu argument –`double`– typ odpovídající parametru –`Money`– dočasnou hodnotou typu `Money` se vytvářejí na základě argument a použít k dokončení volání funkce. Ve třetím volání `display_balance`, Všimněte si, že argument není `double`, ale místo toho `float` s hodnotou `9.99`– a ještě volání funkce můžete stále dokončit, protože kompilátor můžete provést standardní převod – v tomto případě , z `float` k `double`– a poté proveďte převod uživatelem definované `double` k `Money` převod dokončíte tím nezbytné.  
  
### <a name="declaring-conversion-constructors"></a>Deklarování konstruktory převodu  
 Platí následující pravidla pro deklarování konstruktor převod:  
  
-   Cílový typ převodu je typ definovaný uživatelem, který je vytvářen.  
  
-   Konstruktory převodu trvají obvykle právě jeden argument, který je typem zdroje. Konstruktor převod však můžete zadat další parametry, pokud každý další parametr nemá výchozí hodnotu. Typ zdroje zůstane typ prvního parametru.  
  
-   Konstruktory převodu, podobně jako všechny konstruktory, nezadávejte návratovým typem. Určení návratový typ v deklaraci je chyba.  
  
-   Konstruktory převodu může být explicitní.  
  
### <a name="explicit-conversion-constructors"></a>Explicitní převod konstruktory  
 Deklarováním konstruktor převod být `explicit`, ho můžete lze použít pouze k provedení přímé inicializace objektu nebo provést explicitní přetypování. Tím se zabrání funkce, které přijměte argument typu třídy také implicitně přijímat argumenty konstruktoru převod typ zdroje a typu třídy brání v dodržení kopie inicializovat z hodnoty typu zdroje. Následující příklad ukazuje, jak definice explicitní převod konstruktoru, a efekt, který má na jaké kód je ve správném formátu.  
  
```  
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
  
 V tomto příkladu, Všimněte si, že stále můžete použít konstruktor explicitní převod provést přímý inicializace `payable`. Pokud místo toho byste chtěli kopie inicializovat `Money payable = 79.99;`, bude k chybě. První volání `display_balance` není ovlivněn, protože argument je správného typu. Druhé volání `display_balance` se o chybu, protože konstruktor převod nelze použít k provedení implicitní převody. Třetí volání `display_balance` je právní kvůli explicitní přetypování na `Money`, ale Všimněte si, že kompilátor stále pomohl dokončit přetypování vložením implicitní přetypování z `float` k `double`.  
  
 I když pohodlí umožnit implicitní převody může být tempting, to tak můžou představovat pevný nalézt chyby. Pravidlem je, aby všechny konstruktory převodu explicitní s výjimkou případů, kdy jste si jisti, které chcete konkrétní převod proběhnout implicitně.  
  
##  <a name="ConvFunc"></a>Převodní funkce  
 Funkce pro převod definujte převody z uživatelsky definovaný typ. na jiné typy. Tyto funkce jsou někdy označovány jako "operátory přetypování", protože, společně s konstruktory převodu, jsou volány při hodnotu vložena do jiného typu. Následující příklad ukazuje, převod funkci, která převádí z uživatelsky definovaný typ. `Money`, typu předdefinované `double`:  
  
```  
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
  
 Všimněte si, že členské proměnné `amount` přišla privátní a že veřejné převod fungovat na typ `double` uvádíme pouze k vrátí hodnotu `amount`. Ve funkci `display_balance`, dojde k implicitní převod při hodnotě `balance` je streamování na standardní výstup pomocí datového proudu operátor vložení `<<`. Protože pro uživatelem definovaný typ není definována žádná operátor vložení datového proudu `Money`, ale je jedna pro předdefinovaný typ `double`, kompilátor můžete použít funkci pro převod z `Money` k `double` vyhovět vkládání do datového proudu operátor.  
  
 Odvozené třídy jsou děděné funkce pro převod. Funkce pro převod v odvozené třídě přepsat pouze funkce zděděné převodu při převodu do stejného typu. Například převod uživatelem definované funkce odvozené třídy `operator int` nepřepisuje – nebo i vliv – převod uživatelem definované funkce základní třídy `operator short`, i když standardní převody definovat převod vztah mezi `int` a `short`.  
  
### <a name="declaring-conversion-functions"></a>Deklarování převodní funkce  
 Platí následující pravidla pro deklarování funkci pro převod:  
  
-   Cílový typ převodu musí být deklarován před deklaraci funkci pro převod. Třídy, struktury, výčty a definice TypeDef nelze deklarovat v deklaraci funkce převodu.  
  
    ```  
    operator struct String { char string_storage; }() // illegal  
    ```  
  
-   Funkce převodu nepřijímají argumenty. Zadání všech parametrů v deklaraci je chyba.  
  
-   Převodní funkce mají návratový typ, který je zadán název funkce převodu, která je také název převod z typu cíle. Určení návratový typ v deklaraci je chyba.  
  
-   Převodní funkce může být virtuální.  
  
-   Převodní funkce může být explicitní.  
  
### <a name="explicit-conversion-functions"></a>Explicitní převod funkce  
 Pokud funkci pro převod je deklarován jako explicitní, lze použít pouze k provedení explicitní přetypování. Tím se zabrání funkce, které přijměte argument typ cíle funkci pro převod z také implicitně přijímá argumenty typu třídy a instance typu cíle brání v dodržení kopie inicializovat z hodnoty typu třídy. Následující příklad ukazuje, jak definovat explicitní převod funkce a efekt má na to, jaký kód je ve správném formátu.  
  
```  
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
  
 Zde funkci pro převod `operator double` byl proveden explicitní a explicitní přetypování na typ `double` byla zavedena ve funkci `display_balance` provést převod. Pokud toto přetypování byly vynechán, bude kompilátor nelze najít vhodný datový proud vložení operátor `<<` pro typ `Money` a dojde k chybě.  
  
