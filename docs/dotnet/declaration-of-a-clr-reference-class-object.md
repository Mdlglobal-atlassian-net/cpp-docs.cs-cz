---
title: Deklarace objektu referenční třídy CLR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- types [C++], reference types
- reference types, CLR
ms.assetid: 6d64f746-3715-4948-ada3-88859f4150e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 12cead3a142c69da56390ca6f5bf32cecc3b0075
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="declaration-of-a-clr-reference-class-object"></a>Deklarace objektu referenční třídy CLR
Syntaxe deklarace a vytvoří instanci objektu – třída typu odkaz změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Ve spravovaných rozšíření, objekt referenční třídy typu deklarována pomocí syntaxe ukazatele ISO-C++, s nepovinným použitím `__gc` – klíčové slovo nalevo od hvězdičkou (`*`). Tady jsou například celou řadu referenční třída typ objektu deklarace podle syntaxe spravovaných rozšíření:  
  
```  
public __gc class Form1 : public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container __gc *components;  
   Button __gc *button1;  
   DataGrid __gc *myDataGrid;     
   DataSet __gc *myDataSet;  
  
   void PrintValues( Array* myArr ) {  
      System::Collections::IEnumerator* myEnumerator =   
         myArr->GetEnumerator();  
  
      Array *localArray;  
      myArr->Copy(myArr, localArray, myArr->Length);  
   }  
};  
```  
  
 Podle nové syntaxe deklarace objektu referenční třídy typu pomocí nového deklarativního tokenu (`^`) označuje oficiálně jako *sledovací popisovač* a neformálně jako *hat*. (Přídavných jmen sledování znamená, že typu odkazu je umístěn v haldě CLR a proto může transparentně přesouvat umístění během komprimace haldy uvolňování paměti. Sledovací popisovač je za běhu transparentně aktualizován. Jsou dvě podobné koncepce *sledovací odkaz* (`%`) a *vnitřní ukazatel* (`interior_ptr<>`), je to popsáno v [Sémantika typu hodnoty](../dotnet/value-type-semantics.md).  
  
 Primární důvody přesunutí deklarativní syntaxe z opětovného použití syntaxe ukazatele ISO-C++ jsou následující:  
  
-   Použití syntaxe ukazatelů neumožňuje přetížené operátory přímo u referenční objekt. Místo toho jeden museli volání operátor pomocí interní název, například `rV1->op_Addition(rV2)` místo více intuitivní `rV1+rV2`.  
  
-   Počet ukazatel operací, jako je například přetypování a aritmetika ukazatele, není povolený pro objekty uložené ve uvolnění paměti haldě. Představu o lepší sledovací popisovač zachycuje povahu odkazového typu CLR.  
  
 `__gc` Modifikátor na sledovací popisovač je zbytečné a není podporována. Použití samotného objektu nemění; stále přistupuje členy prostřednictvím operátoru volby člena ukazatele (`->`). Zde je ukázka, v předchozím příkladu kódu spravovaných rozšíření přeložit na nové syntaxe:  
  
```  
public ref class Form1: public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container^ components;  
   Button^ button1;  
   DataGrid^ myDataGrid;  
   DataSet^ myDataSet;  
  
   void PrintValues( Array^ myArr ) {  
      System::Collections::IEnumerator^ myEnumerator =  
         myArr->GetEnumerator();  
  
      Array ^localArray;  
      myArr->Copy(myArr, localArray, myArr->Length);   }  
};  
```  
  
## <a name="dynamic-allocation-of-an-object-on-the-clr-heap"></a>Dynamické přidělení objektu v haldě CLR  
 Ve spravovaných rozšíření existují dva `new` výrazy pro přidělení mezi nativní a spravovaná halda byla z velké části transparentní. V téměř všechny instance je možné použít k určení, jestli se má přidělit paměť z nativní nebo spravovaný haldy kontextu kompilátoru. Například  
  
```  
Button *button1 = new Button; // OK: managed heap  
int *pi1 = new int;           // OK: native heap  
Int32 *pi2 = new Int32;       // OK: managed heap  
```  
  
 Pokud nechcete, aby přidělování haldy, může nasměrovat kompilátor buď `__gc` nebo `__nogc` – klíčové slovo. V nové syntaxe oddělená povaha dvou nových výrazů je explicitní uvedení `gcnew` – klíčové slovo. Například předchozí tři deklarace vypadat takto v nové syntaxe:  
  
```  
Button^ button1 = gcnew Button;        // OK: managed heap  
int * pi1 = new int;                   // OK: native heap  
Int32^ pi2 = gcnew Int32; // OK: managed heap  
```  
  
 Zde je inicializace spravovaných rozšíření `Form1` deklarované členy v předchozí části:  
  
```  
void InitializeComponent() {  
   components = new System::ComponentModel::Container();  
   button1 = new System::Windows::Forms::Button();  
   myDataGrid = new DataGrid();  
  
   button1->Click +=   
      new System::EventHandler(this, &Form1::button1_Click);  
}  
```  
  
 Zde je stejná inicializace přepracována do nové syntaxe. Hat není požadovaná pro typ odkazu, pokud je cílem `gcnew` výraz.  
  
```  
void InitializeComponent() {  
   components = gcnew System::ComponentModel::Container;  
   button1 = gcnew System::Windows::Forms::Button;  
   myDataGrid = gcnew DataGrid;  
  
   button1->Click +=   
      gcnew System::EventHandler( this, &Form1::button1_Click );  
}  
```  
  
## <a name="a-tracking-reference-to-no-object"></a>Sledovací odkaz na žádný objekt.  
 V nové syntaxe `0` již představuje adresu hodnotu null, ale je považován za celé číslo, stejně jako `1`, `10`, nebo `100`. Nový token speciální představuje hodnotu null pro sledovací odkaz. Například v spravovaných rozšíření jsme inicializace typu odkazu. Chcete-li vyřešit žádný objekt následujícím způsobem:  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 V nové syntaxe zadejte k jakékoli inicializace nebo přiřazení hodnoty `Object` způsobí, že implicitní zabalení tohoto typu hodnoty. V nové syntaxe obě `obj` a `obj2` jsou inicializovány řešit zabalené objekty Int32, obsahující hodnoty 0 a 1, v uvedeném pořadí. Příklad:  
  
```  
// causes the implicit boxing of both 0 and 1  
Object ^ obj = 0;  
Object ^ obj2 = 1;  
```  
  
 Proto, aby bylo možné provést explicitním inicializačním, přiřazení a porovnání sledovací popisovač na hodnotu null, použijte new – klíčové slovo `nullptr`.  Správné revize původní příkladu vypadá takto:  
  
```  
// OK: we set obj to refer to no object  
Object ^ obj = nullptr;  
  
// OK: we initialize obj2 to a Int32^  
Object ^ obj2 = 1;  
```  
  
 To poněkud ztěžuje portování z existujícího kódu do nové syntaxe. Zvažte například následující deklaraci třídy hodnoty:  
  
```  
__value struct Holder {  
   Holder( Continuation* c, Sexpr* v ) {  
      cont = c;  
      value = v;  
      args = 0;  
      env = 0;  
   }  
  
private:  
   Continuation* cont;  
   Sexpr * value;  
   Environment* env;  
   Sexpr * args __gc [];  
};  
```  
  
 Zde i `args` a `env` jsou odkazové typy CLR. Inicializace těchto dvou členů na `0` v konstruktoru nemůže zůstat beze změny v přechodu do nové syntaxe. Místo toho se musí změnit tak, aby `nullptr`:  
  
```  
value struct Holder {  
   Holder( Continuation^ c, Sexpr^ v )  
   {  
      cont = c;  
      value = v;  
      args = nullptr;  
      env = nullptr;  
   }  
  
private:  
   Continuation^ cont;  
   Sexpr^ value;  
   Environment^ env;  
   array<Sexpr^>^ args;  
};  
```  
  
 Podobně testování členů, jejich porovnání s `0` musí být také změněno k porovnání členy `nullptr`. Tady je syntaxe spravovaných rozšíření:  
  
```  
Sexpr * Loop (Sexpr* input) {  
   value = 0;  
   Holder holder = Interpret(this, input, env);  
  
   while (holder.cont != 0) {  
      if (holder.env != 0) {  
         holder=Interpret(holder.cont,holder.value,holder.env);  
      }  
      else if (holder.args != 0) {  
         holder =   
         holder.value->closure()->  
         apply(holder.cont,holder.args);  
      }  
   }  
  
   return value;  
}  
```  
  
 Tady je revize, nahraďte každý `0` instanci s `nullptr`. Nástroj pro překládání pomáhá v této transformaci automatizací mnoha, není-li všech výskytů, včetně použití `NULL` makro.  
  
```  
Sexpr ^ Loop (Sexpr^ input) {  
   value = nullptr;  
   Holder holder = Interpret(this, input, env);  
  
   while ( holder.cont != nullptr ) {  
      if ( holder.env != nullptr ) {  
         holder=Interpret(holder.cont,holder.value,holder.env);  
      }  
      else if (holder.args != nullptr ) {  
         holder =   
         holder.value->closure()->  
         apply(holder.cont,holder.args);  
      }  
   }  
  
   return value;  
}  
```  
  
 `nullptr` Jsou převedeny na libovolný typ popisovače ukazatel nebo sledování, ale není povýšen na integrální typu. V následující sadu inicializacích, například `nullptr` je platný pouze jako počáteční hodnota pro první dvě.  
  
```  
// OK: we set obj and pstr to refer to no object  
Object^ obj = nullptr;  
char*   pstr = nullptr; // 0 would also work here  
  
// Error: no conversion of nullptr to 0  
int ival = nullptr;  
```  
  
 Podobně dává přetížené sadu metod, jako je následující:  
  
```  
void f( Object^ ); // (1)  
void f( char* );   // (2)  
void f( int );     // (3)  
```  
  
 Vyvolání s `nullptr` literálu, jako je například následující příkaz,  
  
```  
// Error: ambiguous: matches (1) and (2)  
f(  nullptr );  
```  
  
 je nejednoznačné, protože `nullptr` odpovídající sledovací popisovač i ukazatel a neexistuje žádná priorita jeden typ z nich. (Tato situace vyžaduje explicitní přetypování Chcete-li odstranit nejednoznačnost.)  
  
 Vyvolání s `0` přesně odpovídá instanci (3):  
  
```  
// OK: matches (3)  
f( 0 );  
```  
  
 protože `0` je typu integer. Byly `f(int)` nejsou k dispozici, volání by jednoznačně odpovídalo `f(char*)` prostřednictvím standardního převodu. Pravidel porovnávání dávají přednost přesnou shodu přes standardní převod. Chybí přesnou shodu standardní převod má přednost implicitní zabalení typu hodnoty. To je proto nedochází k nejednoznačnosti.  
  
## <a name="see-also"></a>Viz také  
 [Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)   
 [Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Operátor popisovače objektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)