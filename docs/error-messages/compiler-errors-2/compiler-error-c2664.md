---
title: Chyba kompilátoru C2664
ms.date: 11/04/2016
f1_keywords:
- C2664
helpviewer_keywords:
- C2664
ms.assetid: 3595d66e-cf87-4fda-a896-c0cd81f95db4
ms.openlocfilehash: cffd178e1736358333ee27d4572d3531de23f527
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774604"
---
# <a name="compiler-error-c2664"></a>Chyba kompilátoru C2664

'function': nelze převést argument n z 'type1' na 'type2'

Tohoto problému s převodem parametrů může dojít, pokud je vytvořena instance třídy a v konstruktoru označeného klíčovým Probíhá pokus o implicitní převod `explicit` – klíčové slovo. Další informace o explicitních převodů, naleznete v tématu [uživatelem definovaných převodů typu](../../cpp/user-defined-type-conversions-cpp.md).

Pokud dočasný objekt je předán funkci, která má odkaz na objekt jako parametr, musí být tento odkaz `const` odkaz.

Pokud je této funkci předán parametr, který není očekávaného typu, vytvoří se pomocí odpovídajícího konstruktoru dočasný objekt. Tento dočasný objekt je pak předán funkci. V tomto případě slouží dočasný objekt k inicializaci odkazu. Ve starších verzích tohoto jazyka bylo možné přechodnými objekty inicializovat všechny odkazy.

Chcete-li vyřešit upozornění C2664

- Znovu zkontrolujte prototyp dané funkce a opravte argument uvedený v chybové zprávě.

- V případě potřeby zadejte explicitní převod.

K upozornění C2664 může rovněž dojít, pokud třída skrývá člena v jedné ze svých základních tříd.

Další informace najdete v tématu [jak: Převod typu System::String na wchar_t * nebo char\*](../../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md).

## <a name="example"></a>Příklad

Následující ukázka vygeneruje upozornění C2664 a ukazuje, jak ho opravit.

```
// C2664.cpp
// C2664
struct A {
   void f(int i) {};
};

struct B : public A {
   // To fix, uncomment the following line.
   // using A::f;
   void f(A a) {};
};

int main() {
   B b;
   int i = 1;
   b.f(i);   // B::F hides A::f Uncomment the using declaration in B.
}
```

## <a name="example"></a>Příklad

Tato ukázka rovněž vygeneruje upozornění C2664 a ukazuje, jak ho opravit.

```
// C2664b.cpp
// C2664 expected
struct A {
   // To fix, uncomment the following line.
   // A(int i){}
};

void func( int, A ) {}

int main() {
   func( 1, 1 );   // No conversion from int to A.
}
```

## <a name="example"></a>Příklad

Další ukázka demonstruje upozornění C2664 pomocí řetězcového literálu volat `Test`a ukazuje, jak ho opravit. Protože je tento parametr `szString` odkazu, objekt musí být vytvořen příslušným konstruktorem. Výsledkem je dočasný objekt, který nelze použít k inicializaci tohoto odkazu.

```
// C2664c.cpp
// compile with: /EHsc
// C2664 expected
#include <iostream>
#include <string.h>
using namespace std;

class szString {
   int slen;
   char *str;

public:
   szString(const char *);
   int len() const {
      return slen;
   }
};

// Simple reference cannot bind to temp var.
void Test(szString &a) {}

// To fix, uncomment the following line.
// void Test(const szString &a) {}

szString::szString(const char * newstr) : slen(0), str(NULL) {
   slen=strlen(newstr);
   str = new char[slen + 1];
   if (str)
      strcpy_s(str, (slen + 1), newstr);
}

int main() {
   Test("hello");
}
```

## <a name="example"></a>Příklad

Kompilátor vynucuje standardní požadavky jazyka C++ pro použití `const`. Tato ukázka vygeneruje upozornění C2664:

```
// C2664d.cpp
// C2664 expected
#include <windows.h>

void func1(LPCSTR &s)
{

}

void func2(LPSTR &s)
{
   func1(s);
}

int main()
{
   return 0;
}
```

## <a name="example"></a>Příklad

Zde je složitější situace, ve kterém se vygeneruje upozornění C2664, včetně pokyny o tom, jak ho opravit:

```
// C2664e.cpp
// compile with: /EHsc
// C2664 expected
#define _INTL
#include <locale>
#include <iostream>

using namespace std;
#define LEN 90

int main( ) {
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));

   // To fix, delete the following line.
   char* pszNext;

   // To fix, uncomment the following line.
   // const char* pszNext;

   wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).in( state,
      pszExt, &pszExt[strlen(pszExt)], pszNext,
      pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   // See earlier comment.
      pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error) ?
                       L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;

   exit(-1);
}
```

## <a name="example"></a>Příklad

Proměnná výčtu není převedena na svůj podkladový typ tak, aby bylo splněno volání funkce. Další informace najdete v tématu [výčet tříd](../../extensions/enum-class-cpp-component-extensions.md). Následující ukázka vygeneruje upozornění C2664 a ukazuje, jak ho opravit.

```
// C2664f.cpp
// compile with: /clr
using namespace System;
public enum class A : Char {
   None = 0,
   NonSilent = 1,
};

void Test(Char c) {}

int main() {
   A aa = A::None;
   Test(aa);   // C2664
   Test(Char(aa));   // OK - fix by using a conversion cast
}
```

## <a name="example"></a>Příklad

Chyba v kompilátoru midl způsobuje, že typ wchar_t se v knihovně typů vygeneruje jako typ short bez znaménka. Tuto chybu vyřešíte tak, že buď tento typ přetypujete ve zdrojovém kódu jazyka C++, nebo tento typ definujete v souboru idl jako řetězec.

```
// C2664g.idl
import "prsht.idl";

[ object, uuid(8402B8F1-BF7F-4B49-92D4-C2B9DF4543E9) ]

interface IMyObj1 : IUnknown {
   HRESULT  teststr([in, string] wchar_t *wstr);
   HRESULT  testarr([in, size_is(len)] wchar_t wstr[], [in] int len);
   HRESULT  testbstr([in] BSTR bstr);
};

[  uuid(44463307-CBFC-47A6-8B4F-13CD0A83B436) ]
library myproj1 {
   [  version(1.0), uuid(D8622C12-5448-42B8-8F0E-E3AD6B8470C1) ]
   coclass CMyObj1 { interface IMyObj1; };
}
```

Upozornění C2664 se vyvolá také pomocí `wchar_t` během portování kódu z aplikace Visual C++ 6.0 do novějších verzí. V aplikaci Visual C++ 6.0 a starší `wchar_t` byla `typedef` pro `unsigned short` a byl proto implicitně převeden na tento typ. Po Visual C++ 6.0 `wchar_t` je svým vlastním předdefinovaným typem, jak je uvedeno ve standardu jazyka C++ a nadále již není implicitně převést na `unsigned short`. Zobrazit [/Zc: wchar_t (wchar_t je nativní typ)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="example"></a>Příklad

Následující ukázka vygeneruje upozornění C2664 a ukazuje, jak ho opravit.

```
// C2664h.cpp
#import "C2664g.tlb"
using namespace myproj1;

int main() {
   IMyObj1Ptr ptr;

   wchar_t * mybuff = 0;
   BSTR bstr = 0;
   int len;
   ptr->teststr(mybuff);
   ptr->testbstr(bstr);
   ptr->testarr(mybuff, len);   // C2664
   ptr->testarr((unsigned short *)mybuff, len);   // OK - Fix by using a cast
}
```

## <a name="example"></a>Příklad

K upozornění C2664 také dojde, pokud kompilátor nemůže odvodit argumenty šablony.

```
// C2664i.cpp
#include <stdio.h>
template <class T, int iType=0>
class CTypedImg {
public:
   CTypedImg() {}
   void run() {}

   operator CTypedImg<T>& () {
      return *((CTypedImg<T>*)this);
    }
};

template <class t1>
void test(CTypedImg<t1>& myarg) {
   myarg.run();
}

int main() {
   CTypedImg<float,2> img;

   test((CTypedImg<float>&)img);   // OK
   test<float>(img);   // OK
   test(img);   // C2664 - qualify as above to fix
}
```