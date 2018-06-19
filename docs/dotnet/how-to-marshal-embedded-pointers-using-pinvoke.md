---
title: 'Postupy: zařazení vložených ukazatelů pomocí služby PInvoke | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a07c9742c393abe2a6213378ee8963839ab66c90
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134894"
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>Postupy: Zařazení vložených ukazatelů pomocí služby PInvoke
Funkce, které jsou implementované v nespravované knihovny DLL lze volat ze spravovaného kódu pomocí funkce pro vyvolání platformy (P/Invoke). Pokud zdrojový kód pro knihovnu DLL není k dispozici, P/Invoke je jedinou možností pro spolupráci. Na rozdíl od jiných jazyků .NET, poskytuje Visual C++ alternativu k P/Invoke. Další informace najdete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md) a [postupy: zařazení vložených ukazatelů pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).  
  
## <a name="example"></a>Příklad  
 Předávání struktur do nativního kódu vyžaduje vytvořený spravované strukturu, která je ekvivalentní z hlediska rozložení dat nativní struktuře. Struktury, které obsahují ukazatele ale vyžadují speciální zacházení. Pro každý vložený ukazatel ve struktuře nativní spravovaná verze struktury musí obsahovat instanci <xref:System.IntPtr> typu. Navíc paměti pro tyto instance musí být explicitně přidělena, inicializovat a vydání pomocí <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>, <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A>, a <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> metody.  
  
 Následující kód se skládá z nespravovaného a spravovaný modul. Nespravovaný modul je knihovna DLL, která definuje funkci, která přijímá strukturu s názvem ListString, který obsahuje ukazatel a funkci nazvanou TakesListStruct. Spravovaný modul je aplikace příkazového řádku, která importuje funkci TakesListStruct a definuje strukturu s názvem MListStruct, která je ekvivalentní nativní ListStruct s tím rozdílem, že double * je reprezentována pomocí <xref:System.IntPtr> instance. Před voláním TakesListStruct, hlavní funkce přidělí a inicializuje paměti, která odkazuje na toto pole.  
  
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
  
 Všimněte si, že žádná část knihovny DLL je vystaven spravovaného kódu pomocí tradiční #include – direktiva. Ve skutečnosti knihovnu DLL přístupná za běhu, takže problémy s funkcí importovány s <xref:System.Runtime.InteropServices.DllImportAttribute> nebudou zjištěna v době kompilace.  
  
## <a name="see-also"></a>Viz také  
 [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)