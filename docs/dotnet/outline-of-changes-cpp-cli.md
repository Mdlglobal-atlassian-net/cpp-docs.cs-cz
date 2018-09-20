---
title: Přehled změn (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c0bbbd6b-c5c4-44cf-a6ca-c1010c377e9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cfdf502d5529232b856f85a031ff90392d7c2ff0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415119"
---
# <a name="outline-of-changes-ccli"></a>Přehled změn (C++/CLI)

Tato osnovy ukazuje příklady některých změn v jazyce ze spravovaných rozšíření jazyka C++ pro Visual C++. Pomocí následujícího odkazu, který doprovází každé položky pro další informace.

## <a name="no-double-underscore-keywords"></a>Žádná klíčová slova dvojitým podtržítkem

Dvojitým podtržítkem před všechna klíčová slova byla odebrána s jednou výjimkou. Proto `__value` stane `value`, a `__interface` stane `interface`, a tak dále. Aby se zabránilo došlo ke konfliktům názvů mezi klíčovými slovy a identifikátory v uživatelském kódu, jsou považovány klíčová slova především jako kontextové.

Zobrazit [klíčová slova jazyka (C + +/ CLI)](../dotnet/language-keywords-cpp-cli.md) Další informace.

## <a name="class-declarations"></a>Deklarace tříd

Spravovaných rozšíření syntaxe:

```
__gc class Block {};                           // reference class
__value class Vector {};                       // value class
__interface I {};                        // interface class
__gc __abstract class Shape {};                // abstract class
__gc __sealed class Shape2D : public Shape {}; // derived class
```

Nová syntaxe:

```
ref class Block {};                // reference class
value class Vector {};             // value class
interface class I {};        // interface class
ref class Shape abstract {};       // abstract class
ref class Shape2D sealed: Shape{}; // derived class
```

Zobrazit [spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md) Další informace.

## <a name="object-declaration"></a>Deklarace objektu

Spravovaných rozšíření syntaxe:

```
public __gc class Form1 : public System::Windows::Forms::Form {
private:
   System::ComponentModel::Container __gc *components;
   System::Windows::Forms::Button   __gc *button1;
   System::Windows::Forms::DataGrid __gc *myDataGrid;
   System::Data::DataSet  __gc *myDataSet;
};
```

Nová syntaxe:

```
public ref class Form1 : System::Windows::Forms::Form {
   System::ComponentModel::Container^ components;
   System::Windows::Forms::Button^ button1;
   System::Windows::Forms::DataGrid^ myDataGrid;
   System::Data::DataSet^ myDataSet;
};
```

Zobrazit [deklarace objektu referenční třídy CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) Další informace.

### <a name="managed-heap-allocation"></a>Spravovaná velikost haldy

Spravovaných rozšíření syntaxe:

```
Button* button1 = new Button; // managed heap
int *pi1 = new int;           // native heap
Int32 *pi2 = new Int32;       // managed heap
```

Nová syntaxe:

```
Button^ button1 = gcnew Button;        // managed heap
int * pi1 = new int;                   // native heap
Int32^ pi2 = gcnew Int32;              // managed heap
```

Zobrazit [deklarace objektu referenční třídy CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) Další informace.

### <a name="a-tracking-reference-to-no-object"></a>Odkaz sledování na žádný objekt.

Spravovaných rozšíření syntaxe:

```
// OK: we set obj to refer to no object
Object * obj = 0;

// Error: no implicit boxing
Object * obj2 = 1;
```

Nová syntaxe:

```
// Incorrect Translation
// causes the implicit boxing of both 0 and 1
Object ^ obj = 0;
Object ^ obj2 = 1;

// Correct Translation
// OK: we set obj to refer to no object
Object ^ obj = nullptr;

// OK: we initialize obj2 to an Int32^
Object ^ obj2 = 1;
```

Zobrazit [deklarace objektu referenční třídy CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) Další informace.

## <a name="array-declaration"></a>Deklarace pole

Pole CLR jsme přepracovali. Je podobný stl `vector` kolekce šablony, ale maps na základní `System::Array` třídy – to znamená, že není implementace šablony.

Zobrazit [deklarace pole CLR](../dotnet/declaration-of-a-clr-array.md) Další informace.

### <a name="array-as-parameter"></a>Pole jako parametr

Spravovaných rozšíření syntaxe pole:

```
void PrintValues( Object* myArr __gc[]);
void PrintValues( int myArr __gc[,,]);
```

Nová syntaxe pole:

```
void PrintValues( array<Object^>^ myArr );
void PrintValues( array<int,3>^ myArr );
```

### <a name="array-as-return-type"></a>Pole jako návratový typ

Spravovaných rozšíření syntaxe pole:

```
Int32 f() [];
int GetArray() __gc[];
```

Nová syntaxe pole:

```
array<Int32>^ f();
array<int>^ GetArray();
```

### <a name="shorthand-initialization-of-local-clr-array"></a>Zkrácený tvar vlastností inicializace pole místní CLR

Spravovaných rozšíření syntaxe pole:

```
int GetArray() __gc[] {
   int a1 __gc[] = { 1, 2, 3, 4, 5 };
   Object* myObjArray __gc[] = { __box(26), __box(27), __box(28),
                                 __box(29), __box(30) };

   return a1;
}
```

Nová syntaxe pole:

```
array<int>^ GetArray() {
   array<int>^ a1 = {1,2,3,4,5};
   array<Object^>^ myObjArray = {26,27,28,29,30};

   return a1;
}
```

### <a name="explicit-clr-array-declaration"></a>Deklarace pole CLR explicitní

Spravovaných rozšíření syntaxe pole:

```
Object* myArray[] = new Object*[2];
String* myMat[,] = new String*[4,4];
```

Nová syntaxe pole:

```
array<Object^>^ myArray = gcnew array<Object^>(2);
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);
```

Nový jazyk: explicitní inicializace pole, která následuje gcnew

```
// explicit initialization list follow gcnew
// is not supported in Managed Extensions
array<Object^>^ myArray =
   gcnew array<Object^>(4){ 1, 1, 2, 3 };
```

## <a name="scalar-properties"></a>Skalární vlastnosti

Syntaxe vlastností spravovaného rozšíření:

```
public __gc __sealed class Vector {
   double _x;

public:
   __property double get_x(){ return _x; }
   __property void set_x( double newx ){ _x = newx; }
};
```

Nová syntaxe vlastnosti:

```
public ref class Vector sealed {
   double _x;

public:
   property double x
   {
      double get()             { return _x; }
      void   set( double newx ){ _x = newx; }
   } // Note: no semi-colon
};
```

Nový jazyk: triviální vlastnosti

```
public ref class Vector sealed {
public:
   // equivalent shorthand property syntax
   // backing store is not accessible
   property double x;
};
```

Zobrazit [deklaraci vlastnosti](../dotnet/property-declaration.md) Další informace.

## <a name="indexed-properties"></a>Indexované vlastnosti

Spravovaná rozšíření syntaxe indexované vlastnosti:

```
public __gc class Matrix {
   float mat[,];

public:
   __property void set_Item( int r, int c, float value) { mat[r,c] = value; }
   __property int get_Item( int r, int c ) { return mat[r,c]; }
};
```

Nová syntaxe indexovanou vlastnost:

```
public ref class Matrix {
   array<float, 2>^ mat;

public:
   property float Item [int,int] {
      float get( int r, int c ) { return mat[r,c]; }
      void set( int r, int c, float value ) { mat[r,c] = value; }
   }
};
```

Nový jazyk: indexované vlastnosti na úrovni třídy

```
public ref class Matrix {
   array<float, 2>^ mat;

public:
   // ok: class level indexer now
   //     Matrix mat;
   //     mat[ 0, 0 ] = 1;
   //
   // invokes the set accessor of the default indexer

   property float default [int,int] {
      float get( int r, int c ) { return mat[r,c]; }
      void set( int r, int c, float value ) { mat[r,c] = value; }
   }
};
```

Zobrazit [deklarace indexu vlastnosti](../dotnet/property-index-declaration.md) Další informace.

## <a name="overloaded-operators"></a>Přetížené operátory

Syntaxe přetíženého operátoru spravované rozšíření:

```
public __gc __sealed class Vector {
public:
   Vector( double x, double y, double z );

   static bool    op_Equality( const Vector*, const Vector* );
   static Vector* op_Division( const Vector*, double );
};

int main() {
   Vector *pa = new Vector( 0.231, 2.4745, 0.023 );
   Vector *pb = new Vector( 1.475, 4.8916, -1.23 );

   Vector *pc = Vector::op_Division( pa, 4.8916 );

   if ( Vector::op_Equality( pa, pc ))
      ;
}
```

Nová syntaxe přetíženého operátoru:

```
public ref class Vector sealed {
public:
   Vector( double x, double y, double z );

   static bool    operator ==( const Vector^, const Vector^ );
   static Vector^ operator /( const Vector^, double );
};

int main() {
   Vector^ pa = gcnew Vector( 0.231, 2.4745, 0.023 );
   Vector^ pb = gcnew Vector( 1.475, 4.8916, -1.23 );

   Vector^ pc = pa / 4.8916;
   if ( pc == pa )
      ;
}
```

Zobrazit [přetížené operátory](../dotnet/overloaded-operators.md) Další informace.

## <a name="conversion-operators"></a>Operátory převodu

Syntaxe operátor převodu spravovaného rozšíření:

```
__gc struct MyDouble {
   static MyDouble* op_Implicit( int i );
   static int op_Explicit( MyDouble* val );
   static String* op_Explicit( MyDouble* val );
};
```

Nová syntaxe operátoru převodu:

```
ref struct MyDouble {
public:
   static operator MyDouble^ ( int i );
   static explicit operator int ( MyDouble^ val );
   static explicit operator String^ ( MyDouble^ val );
};
```

Zobrazit [změny u operátorů převodů](../dotnet/changes-to-conversion-operators.md) Další informace.

## <a name="explicit-override-of-an-interface-member"></a>Explicitní přepsání člena rozhraní

Spravovaná rozšíření explicitní přepsání syntaxi:

```
public __gc class R : public ICloneable {
   // to be used through ICloneable
   Object* ICloneable::Clone();

   // to be used through an R
   R* Clone();
};
```

Nová syntaxe explicitního přepsání:

```
public ref class R : public ICloneable {
   // to be used through ICloneable
   virtual Object^ InterfaceClone() = ICloneable::Clone;

   // to be used through an R
   virtual R^ Clone();
};
```

Zobrazit [explicitní přepsání člena rozhraní](../dotnet/explicit-override-of-an-interface-member.md) Další informace.

## <a name="private-virtual-functions"></a>Soukromé virtuální funkce

Soukromé virtuální funkce syntaxe spravovaného rozšíření:

```
__gc class Base {
private:
   // inaccessible to a derived class
   virtual void g();
};

__gc class Derived : public Base {
public:
   // ok: g() overrides Base::g()
   virtual void g();
};
```

Novou syntaxi soukromé virtuální funkce

```
ref class Base {
private:
   // inaccessible to a derived class
   virtual void g();
};

ref class Derived : public Base {
public:
   // error: cannot override: Base::g() is inaccessible
   virtual void g() override;
};
```

Zobrazit [soukromé virtuální funkce](../dotnet/private-virtual-functions.md) Další informace.

## <a name="clr-enum-type"></a>Typ enum v prostředí CLR

Syntaxe spravovaného rozšíření výčtu:

```
__value enum e1 { fail, pass };
public __value enum e2 : unsigned short  {
   not_ok = 1024,
   maybe, ok = 2048
};
```

Nová syntaxe výčtu:

```
enum class e1 { fail, pass };
public enum class e2 : unsigned short {
   not_ok = 1024,
   maybe, ok = 2048
};
```

Kromě malých syntaktické změnit chování typu výčtu CLR nebylo změněno v několika způsoby:

- Dopředná deklarace výčtu CLR je již nejsou podporovány.

- Řešení přetížení mezi předdefinované aritmetické typy a hierarchie třídy objektu má obrácený mezi spravovaných rozšíření a Visual C++. Jako vedlejší efekt se už nebude implicitně převést výčtech CLR pro aritmetické typy.

- V nové syntaxi výčtu CLR udržuje svůj vlastní obor, což není případ spravovaných rozšíření. Dříve byly enumerátory viditelné v rámci rozsah výčtu; enumerátory jsou teď zapouzdřeny v rámci rozsahu výčtového typu.

Zobrazit [Výčtový typ CLR](../dotnet/clr-enum-type.md) Další informace.

## <a name="removal-of-box-keyword"></a>Odebrání __box – klíčové slovo

Spravovaná rozšíření zabalení syntaxi:

```
Object *o = __box( 1024 ); // explicit boxing
```

Nové zabalení syntaxi:

```
Object ^o = 1024; // implicit boxing
```

Zobrazit [sledování A zpracování na hodnotu v poli](../dotnet/a-tracking-handle-to-a-boxed-value.md) Další informace.

## <a name="pinning-pointer"></a>Ukazatel Připnutí

Spravovaná rozšíření Připnutí syntaxe ukazatele:

```
__gc struct H { int j; };

int main() {
   H * h = new H;
   int __pin * k = & h -> j;
};
```

Nová syntaxe připnutý ukazatele:

```
ref struct H { int j; };

int main() {
   H^ h = gcnew H;
   pin_ptr<int> k = &h->j;
}
```

Zobrazit [Sémantika typu hodnoty](../dotnet/value-type-semantics.md) Další informace.

## <a name="typeof-keyword-becomes-typeid"></a>__typeof – klíčové slovo bude identifikátor typeid.

Syntaxe typeof spravovaného rozšíření:

```
Array* myIntArray =
   Array::CreateInstance( __typeof(Int32), 5 );
```

Nová syntaxe typeid:

```
Array^ myIntArray =
   Array::CreateInstance( Int32::typeid, 5 );
```

Zobrazit [typeof přechází na T::typeid](../dotnet/typeof-goes-to-t-typeid.md) Další informace.

## <a name="see-also"></a>Viz také

[Základy migrace v jazyce C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)

