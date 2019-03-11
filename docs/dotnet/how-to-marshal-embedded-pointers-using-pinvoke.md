---
title: 'Postupy: Zařazení vložených ukazatelů pomocí služby PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
ms.openlocfilehash: 943a1a2784a37353157cd38da7ebdc9827006fe5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738754"
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>Postupy: Zařazení vložených ukazatelů pomocí služby PInvoke

Funkce, které jsou implementovány v nespravovaných knihoven DLL lze volat ze spravovaného kódu pomocí vyvolání platformy (nespravovaného) funkce. Pokud není k dispozici zdrojový kód pro knihovnu DLL, P/Invoke je jedinou možností pro spolupráci. Ale na rozdíl od jiných jazyků .NET, Visual C++ poskytuje alternativu k P/Invoke. Další informace najdete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md) a [jak: Zařazení vložených ukazatelů pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

## <a name="example"></a>Příklad

Předávání struktur do nativního kódu vyžaduje, že je vytvořena spravovaná struktura, která je ekvivalentní z hlediska rozložení dat nativní struktury. Struktury, které obsahují ukazatele, ale vyžadují speciální zacházení. Pro každý vložený ukazatel ve struktuře nativní, spravované verzi struktury by měl obsahovat instanci <xref:System.IntPtr> typu. Navíc paměti pro tyto instance musí být explicitně přiděleny, inicializovat a uvolněna pomocí <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>, <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A>, a <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> metody.

Následující kód se skládá z nespravovaného a spravovaný modul. Nespravovaný modul je knihovnu DLL, která definuje funkci, která přijme strukturu s názvem ListString, který obsahuje ukazatel a funkci s názvem TakesListStruct. Spravovaný modul je aplikace příkazového řádku, který importuje TakesListStruct funkce a definuje strukturu s názvem MListStruct, která je ekvivalentní nativní ListStruct s tím rozdílem, že dvojité * je reprezentována pomocí <xref:System.IntPtr> instance. Před voláním TakesListStruct hlavní funkci přiděluje a inicializuje přidělenou paměť, která odkazuje na toto pole.

```cpp
// TraditionalDll6.cpp
// compile with: /EHsc /LD
#include <stdio.h>
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct ListStruct {
   int count;
   double* item;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API void TakesListStruct(ListStruct);
}

void TakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}
```

```cpp
// EmbeddedPointerMarshalling.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MListStruct {
   int count;
   IntPtr item;
};

value struct TraditionalDLL {
    [DllImport("TraditionalDLL6.dll")]
   static public void TakesListStruct(MListStruct);
};

int main() {
   array<double>^ parray = gcnew array<double>(10);
   Console::WriteLine("[managed] count = {0}", parray->Length);

   Random^ r = gcnew Random();
   for (int i=0; i<parray->Length; i++) {
      parray[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, parray[i]);
   }

   int size = Marshal::SizeOf(double::typeid);
   MListStruct list;
   list.count = parray->Length;
   list.item = Marshal::AllocCoTaskMem(size * parray->Length);

   for (int i=0; i<parray->Length; i++) {
      IntPtr t = IntPtr(list.item.ToInt32() + i * size);
      Marshal::StructureToPtr(parray[i], t, false);
   }

   TraditionalDLL::TakesListStruct( list );
   Marshal::FreeCoTaskMem(list.item);
}
```

Všimněte si, že není žádná část knihovny DLL zpřístupněna spravovaného kódu pomocí tradiční #include. Ve skutečnosti se knihovny DLL přistupuje za běhu pouze, takže problémy s funkcí importovány s <xref:System.Runtime.InteropServices.DllImportAttribute> nebudou zjištěna v době kompilace.

## <a name="see-also"></a>Viz také:

[Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
