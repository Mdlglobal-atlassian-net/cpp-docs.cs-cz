---
title: ". Zpracování souboru XML | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: XML documentation, processing XML file
ms.assetid: e70fdeae-80ac-4872-ab24-771c5635cfbf
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3a1c0ced45fc7f9c4e51a5dbe8a888c030a6b957
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="xml-file-processing"></a>Zpracování souboru XML
Kompilátor generuje řetězec ID pro každý konstrukce ve vašem kódu, který se označí ke generování dokumentace. Další informace najdete v tématu [doporučené značky dokumentační komentáře](../ide/recommended-tags-for-documentation-comments-visual-cpp.md). ID řetězec jednoznačně identifikuje konstruktu. Programy, které zpracovávají soubor .xml můžete použít ID řetězec k identifikaci odpovídající rozhraní .NET Framework metadata nebo reflexe položky na které se vztahuje na dokumentaci.  
  
 Soubor .xml není znázornění hierarchické kódu, je jako plochý seznam s generovaného ID pro každý prvek.  
  
 Kompilátor dodržuje následující pravidla, když ji vygeneruje ID řetězce:  
  
-   Bez mezer je umístěn v řetězci.  
  
-   První část řetězec ID identifikuje druh člen, které jsou označené pomocí jednoho znaku následovaným dvojtečkou. Se používají následující typy členů:  
  
    |Znak|Popis|  
    |---------------|-----------------|  
    |N|– obor názvů<br /><br /> Dokumentační komentáře nelze přidat do oboru názvů, je možné, cref odkazy na obor názvů.|  
    |T|Typ: třída, rozhraní, struktura, enum, delegát|  
    |D|– definice typedef|  
    |F|pole|  
    |P|vlastnosti (včetně indexery nebo jiných indexované vlastnosti)|  
    |M|(včetně takových speciální metody jako konstruktory, operátory a tak dále) – metoda|  
    |E|event|  
    |!|Řetězec chyby.<br /><br /> Zbývající řetězec poskytuje informace o této chybě. Visual C++ compiler generuje informace o chybě pro odkazy, které nelze vyřešit.|  
  
-   Druhá část řetězce, který je plně kvalifikovaný název položky začínající na kořen oboru názvů. Název položky, jeho nadřazených typ nebo typy a obor názvů jsou odděleny tečkami. Pokud má název samotné položky období, se nahrazují znak hash (#). Předpokládá se, že žádná položka má symbolem hash přímo v jeho názvu. Třeba plně kvalifikovaný název `String` konstruktor by "System.String.#ctor".  
  
-   Pro vlastnosti a metody Pokud jsou argumenty pro metodu, seznam argumentů uzavřený v závorkách následuje. Pokud neexistují žádné argumenty, jsou k dispozici žádné závorek. Argumenty, které jsou oddělené čárkami. Kódování každý argument dodržuje přímo jak je zakódován v rozhraní .NET Framework podpis:  
  
    -   Základní typy. Regulární typy (ELEMENT_TYPE_CLASS nebo Typ ELEMENT_TYPE_VALUETYPE, který), jsou reprezentovány jako plně kvalifikovaný název typu.  
  
    -   Vnitřní typy (například ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF. a ELEMENT_TYPE_VOID) jsou reprezentovány jako plně kvalifikovaný název odpovídající úplné typu, například **System.Int32** nebo **System.TypedReference**.  
  
    -   ELEMENT_TYPE_PTR je reprezentován jako ' *' následující změny typu.  
  
    -   Typu ELEMENT_TYPE_BYREF je reprezentován jako ' @' následující změny typu.  
  
    -   ELEMENT_TYPE_PINNED je reprezentován jako ' ^' následující změny typu. Visual C++ compiler nikdy vygeneruje.  
  
    -   ELEMENT_TYPE_CMOD_REQ je reprezentován jako "&#124; a plně kvalifikovaný název třídy modifikátor následující změny typu. Visual C++ compiler nikdy vygeneruje.  
  
    -   ELEMENT_TYPE_CMOD_OPT je reprezentován jako '!' a plně kvalifikovaný název třídy modifikátor následující změny typu.  
  
    -   ELEMENT_TYPE_SZARRAY je reprezentován jako ["]" následující element typ pole.  
  
    -   ELEMENT_TYPE_GENERICARRAY je reprezentován jako "[?]" následující element typ pole. Visual C++ compiler nikdy vygeneruje.  
  
    -   ELEMENT_TYPE_ARRAY je reprezentován jako [*dolní hranice*:`size`,*dolní hranice*:`size`] kde je počet čárkami pořadí - 1 a dolní meze a velikost každé dimenze, pokud Označuje, jsou reprezentovány v desítkové soustavě. Pokud není zadán dolní mez nebo velikost, je jednoduše vynechán. Pokud byly vynechány dolní mez a velikosti pro konkrétní dimenzi, ':' je také vynechán. Například dimenzionální 2 pole s 1 jako neurčené velikost a dolní meze je [1:, 1:].  
  
    -   ELEMENT_TYPE_FNPTR je reprezentován jako "= FUNC:`type`(*podpis*)", kde `type` je návratový typ a *podpis* je argumenty metody. Pokud neexistují žádné argumenty, jsou závorky vynechat. Visual C++ compiler nikdy vygeneruje.  
  
     Následující součásti podpis nenachází vzhledem k tomu, že se nikdy používají rozdílné přetížené metody:  
  
    -   Konvence volání  
  
    -   Návratový typ  
  
    -   TYP ELEMENT_TYPE_SENTINEL  
  
-   Pro operátory převodu návratovou hodnotu metody zakódován ' ~' následuje návratový typ, kódovaný jako dříve.  
  
-   Pro obecné typy název typu bude následovat back značek a pak číslo určující počet parametrů obecného typu.  Například  
  
    ```  
    <member name="T:MyClass`2">  
    ```  
  
     Pro typ, který je definován jako `public class MyClass<T, U>`.  
  
     Pro metody trvá obecné typy jako parametry, jsou parametry obecného typu zadané jako čísla, kterými back rysky (například \`0, \`1).  Každý číslo představující zápis pole s nulovým základem pro obecné parametry typu..  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak ID řetězce pro třídu a její členy by vytvořilo.  
  
```  
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