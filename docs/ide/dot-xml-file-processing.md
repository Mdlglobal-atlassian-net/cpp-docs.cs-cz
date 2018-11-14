---
title: Zpracování souboru XML
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation, processing XML file
ms.assetid: e70fdeae-80ac-4872-ab24-771c5635cfbf
ms.openlocfilehash: bc9aa57ffd68630d0a4209f8f8611882f8f36fc3
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524167"
---
# <a name="xml-file-processing"></a>Zpracování souboru XML

Kompilátor generuje řetězec ID pro každý konstrukce ve vašem kódu, který je označený ke generování dokumentace. Další informace najdete v tématu [doporučené značky dokumentační komentáře](../ide/recommended-tags-for-documentation-comments-visual-cpp.md). Řetězec ID jednoznačně identifikuje konstrukce. Programy, které zpracování souboru XML slouží k identifikaci odpovídající rozhraní .NET Framework metadata nebo reflexe položky ke kterému se vztahuje na dokumentaci ID řetězce.

Soubor XML není Hierarchická reprezentace kódu, je seznam bez stromové struktury s vygenerované ID pro každý prvek.

Při generování ID řetězce, kompilátor dodržuje následující pravidla:

- Žádné jiné mezery, nachází v řetězci.

- První část řetězec ID identifikuje typ členu, identifikují se jeden znak následovaný dvojtečkou. Se používají následující typy členů:

  | Znak | Popis |
  |---------------|-----------------|
  | N | – obor názvů<br /><br /> Dokumentační komentáře nelze přidat do oboru názvů, je možné cref odkazy na obor názvů. |
  | T | Typ: třída, rozhraní, struktury, výčtu, delegát |
  | D | – definice typedef |
  | F | pole |
  | P | vlastnosti (včetně indexery nebo jiných indexované vlastnosti) |
  | M | (včetně speciálních metod, jako konstruktory, operátory a tak dále) – metoda |
  | E | event |
  | ! | Text chyby<br /><br /> Zbývající řetězec poskytuje informace o této chybě. Kompilátor Visual C++ generuje informace o chybě pro odkazy, které nelze rozpoznat. |

- Druhá část řetězce je plně kvalifikovaný název položky, počínaje kořenový obor názvů. Název položky, jeho nadřazeného typu nebo typů a obor názvů jsou odděleny tečkami. Pokud má název samotné položky období, budou nahrazeny jako znak hash (#). Předpokládá se, že nemá žádná položka znak hash přímo ve svém názvu. Například plně kvalifikovaný název `String` konstruktor by "System.String.#ctor".

- Vlastnosti a metody Pokud jsou argumenty metody, uzavřený do závorek seznamu argumentů se řídí. Pokud neexistují žádné argumenty, jsou k dispozici žádné závorky. Argumenty jsou odděleny čárkami. Kódování každý argument následuje přímo jak je zakódovaný v rozhraní .NET Framework podpisu:

  - Základní typy. Pravidelné typy (za řetězcem ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE) jsou reprezentovány ve formě plně kvalifikovaný název typu.

  - Vnitřní typy (například ELEMENT_TYPE_I4 ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF. a ELEMENT_TYPE_VOID) jsou reprezentovány ve formě plně kvalifikovaný název odpovídající úplný typ, například **System.Int32** nebo **System.TypedReference**.

  - Typ ELEMENT_TYPE_PTR je vyjádřena jako "*" následující typ změny.

  - ELEMENT_TYPE_BYREF je vyjádřena jako "\@' následující typ změny.

  - ELEMENT_TYPE_PINNED je vyjádřena jako ' ^' následující typ změny. Kompilátor Visual C++ generuje nikdy to.

  - ELEMENT_TYPE_CMOD_REQ je vyjádřena jako "&#124;" a plně kvalifikovaný název třídy modifikátor následující typ změny. Kompilátor Visual C++ generuje nikdy to.

  - ELEMENT_TYPE_CMOD_OPT je vyjádřena jako '!' a plně kvalifikovaný název třídy modifikátor následující typ změny.

  - ELEMENT_TYPE_SZARRAY je reprezentován jako "[]" za typ prvku pole.

  - "[?]" Představuje ELEMENT_TYPE_GENERICARRAY následující typ prvku pole. Kompilátor Visual C++ generuje nikdy to.

  - ELEMENT_TYPE_ARRAY je vyjádřena jako [*dolní hranice*:`size`,*dolní hranice*:`size`] kde je počet čárkami pořadí - 1 a dolní meze a velikosti jednotlivých rozměrů, pokud známé, jsou reprezentovány v desítkové soustavě. Pokud není zadán dolní mez nebo velikost, je jednoduše vynechán. Pokud jsou vynechány dolní mez a velikosti pro konkrétní dimenzi, ":" je také vynechán. Je třeba 2rozměrné pole s 1 jako dolní mez a neurčené formáty [1:, 1:].

  - Typ ELEMENT_TYPE_FNPTR je reprezentován jako "= FUNC:`type`(*podpis*)", kde `type` je návratový typ a *podpis* je argumenty metody. Pokud neexistují žádné argumenty, jsou vynechány závorky. Kompilátor Visual C++ generuje nikdy to.

  Následující součásti podpis nejsou zastoupeny, protože se používají nikdy odlišující přetížené metody:

  - Konvence volání

  - Návratový typ

  - TYP ELEMENT_TYPE_SENTINEL

- Pro operátory převodu je návratová hodnota metody zakódován jako "~" a návratový typ jako již kódovaný.

- Pro obecné typy název typu bude následovat back čárka a potom číslo určující počet parametrů obecného typu.  Například

    ```xml
    <member name="T:MyClass`2">
    ```

  Pro typ, který je definován jako `public class MyClass<T, U>`.

  Pro metody, přičemž obecné typy jako parametry, parametry obecného typu jsou zadané jako čísla začíná back značky (například \`0, \`1).  Každé číslo představující zápis založený na nule pole pro parametry obecného typu.

## <a name="example"></a>Příklad

Následující příklady ukazují, jak ID řetězce pro třídu a její členy by se vygenerovala.

```cpp
// xml_id_strings.cpp
// compile with: /clr /doc /LD
///
namespace N {
// "N:N"

   /// <see cref="System" />
   //  <see cref="N:System"/>
   ref class X {
   // "T:N.X"

   protected:
      ///
      !X(){}
      // "M:N.X.Finalize", destructor's representation in metadata

   public:
      ///
      X() {}
      // "M:N.X.#ctor"

      ///
      static X() {}
      // "M:N.X.#cctor"

      ///
      X(int i) {}
      // "M:N.X.#ctor(System.Int32)"

      ///
      ~X() {}
      // "M:N.X.Dispose", Dispose function representation in metadata

      ///
      System::String^ q;
      // "F:N.X.q"

      ///
      double PI;
      // "F:N.X.PI"

      ///
      int f() { return 1; }
      // "M:N.X.f"

      ///
      int bb(System::String ^ s, int % y, void * z) { return 1; }
      // "M:N.X.bb(System.String,System.Int32@,System.Void*)"

      ///
      int gg(array<short> ^ array1, array< int, 2 >^ IntArray) { return 0; }
      // "M:N.X.gg(System.Int16[], System.Int32[0:,0:])"

      ///
      static X^ operator+(X^ x, X^ xx) { return x; }
     // "M:N.X.op_Addition(N.X,N.X)"

      ///
      property int prop;
      // "M:N.X.prop"

      ///
      property int prop2 {
      // "P:N.X.prop2"

         ///
         int get() { return 0; }
         // M:N.X.get_prop2

         ///
         void set(int i) {}
         // M:N.X.set_prop2(System.Int32)
      }

      ///
      delegate void D(int i);
      // "T:N.X.D"

      ///
      event D ^ d;
      // "E:N.X.d"

      ///
      ref class Nested {};
      // "T:N.X.Nested"

      ///
      static explicit operator System::Int32 (X x) { return 1; }
      // "M:N.X.op_Explicit(N.X!System.Runtime.CompilerServices.IsByValue)~System.Int32"
   };
}
```

## <a name="see-also"></a>Viz také

[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)