---
title: "Postupy: vystavení kontejneru STL/CLR ze sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 84505edf0877a5ae20d28906dde7f4c709574034
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>Postupy: Vystavení kontejneru STL/CLR ze sestavení
STL/CLR – kontejnery, jako `list` a `map` jsou implementované jako třídy ref šablon. Protože jsou C++ šablony vytvořeny v době kompilace, dvě šablony třídy, které přesně stejným podpisem, ale jsou v různých sestavení jsou ve skutečnosti různých typů. To znamená, že šablona třídy nelze použít napříč hranicemi sestavení.  
  
 Chcete-li mezi sestaveními sdílení možná, STL/CLR – kontejnery implementovat obecné rozhraní <xref:System.Collections.Generic.ICollection%601>. Pomocí této obecné rozhraní, všechny jazyky, které podporují obecné typy, včetně C++, C# a Visual Basic, mají přístup k STL/CLR – kontejnery.  
  
 Toto téma ukazuje, jak zobrazit elementy několik kontejnerů STL/CLR, které jsou napsané v C++ sestavení s názvem `StlClrClassLibrary`. Ukážeme dvou sestavení pro přístup k `StlClrClassLibrary`. První sestavení je napsán v C++ a druhý v jazyce C#.  
  
 Pokud obě sestavení jsou napsané v jazyce C++, máte přístup k rozhraní obecné kontejneru, pomocí jeho `generic_container` typedef. Například, pokud máte kontejner typu `cliext::vector<int>`, pak je jeho obecné rozhraní: `cliext::vector<int>::generic_container`. Podobně můžete získat iterovat přes obecné rozhraní pomocí `generic_iterator` typedef, jako v: `cliext::vector<int>::generic_iterator`.  
  
 Vzhledem k tomu, že jsou tyto definice TypeDef deklarované v C++ – soubory hlaviček, nelze je použít sestavení, které jsou napsané v dalších jazycích. Proto generické rozhraní pro přístup k `cliext::vector<int>` v C# nebo kterémkoli jazyce platformy .NET, použijte `System.Collections.Generic.ICollection<int>`. Chcete-li iterace v této kolekci, použijte `foreach` smyčky.  
  
 Následující tabulka uvádí obecné rozhraní, který implementuje každý kontejner STL/CLR:  
  
|Kontejneru STL/CLR|Obecné rozhraní|  
|------------------------|-----------------------|  
|deque < T\>|ICollection < T\>|  
|hash_map – < tisíc, V >|IDictionary < tisíc, V >|  
|hash_multimap < tisíc, V >|IDictionary < tisíc, V >|  
|hash_multiset – < T\>|ICollection < T\>|  
|hash_set – < T\>|ICollection < T\>|  
|Seznam < T\>|ICollection < T\>|  
|Mapa < tisíc, V >|IDictionary < tisíc, V >|  
|multimap < tisíc, V >|IDictionary < tisíc, V >|  
|multimnožina < T\>|ICollection < T\>|  
|nastavit < T\>|ICollection < T\>|  
|Vector < T\>|ICollection < T\>|  
  
> [!NOTE]
>  Protože `queue`, `priority_queue`, a `stack` kontejnery nepodporují iterátory, neimplementuje obecná rozhraní a nemůže být přístupu mezi sestaveními.  
  
## <a name="example-1"></a>Příklad 1  
  
### <a name="description"></a>Popis  
 V tomto příkladu jsme deklarovat C++ třídu, která obsahuje data člena privátní STL/CLR. Potom jsme deklarovat veřejné metody k udělení přístupu k soukromých kolekcí třídy. Tomu se dvěma různými způsoby, jeden pro klienty C++ a jeden pro ostatní klienty .NET.  
  
### <a name="code"></a>Kód  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="example-2"></a>Příklad 2  
  
### <a name="description"></a>Popis  
 V tomto příkladu jsme implementovat třídu deklarované v příkladu 1. Aby klienti budou používat tato knihovna tříd, můžeme použít nástroj manifestu **mt.exe** pro vložení souboru manifestu do knihovny DLL. Podrobnosti najdete v tématu komentáře kódu.  
  
 Další informace o manifestu nástroj a souběžně sdílená sestavení najdete v tématu [izolovaných aplikací C/C++ sestavování a souběžně sdílená sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md).  
  
### <a name="code"></a>Kód  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="example-3"></a>Příklad 3  
  
### <a name="description"></a>Popis  
 V tomto příkladu vytvoříme C++ klienta, který používá knihovny tříd, které jsou vytvořené v příklady 1 a 2. Tento klient použije `generic_container` – definice TypeDef kontejnerů STL/CLR Iterujte přes kontejnery a zobrazit jejich obsah.  
  
### <a name="code"></a>Kód  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="output"></a>Výstup  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
## <a name="example-4"></a>Příklad 4  
  
### <a name="description"></a>Popis  
 V tomto příkladu vytvoříme klienta C#, který používá knihovny tříd, které jsou vytvořené v příklady 1 a 2. Tento klient použije <xref:System.Collections.Generic.ICollection%601> metody kontejnerů STL/CLR Iterujte přes kontejnery a zobrazit jejich obsah.  
  
### <a name="code"></a>Kód  
  
```  
// CsConsoleApp.cs  
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll  
  
using System;  
using System.Collections.Generic;  
using StlClrClassLibrary;  
using cliext;  
  
namespace CsConsoleApp  
{  
    class Program  
    {  
        static int Main(string[] args)  
        {  
            StlClrClass theClass = new StlClrClass();  
  
            Console.WriteLine("cliext::deque contents:");  
            ICollection<char> iCollChar = theClass.GetDequeCs();  
            foreach (char c in iCollChar)  
            {  
                Console.WriteLine(c);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::list contents:");  
            ICollection<float> iCollFloat = theClass.GetListCs();  
            foreach (float f in iCollFloat)  
            {  
                Console.WriteLine(f);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::map contents:");  
            IDictionary<int, string> iDict = theClass.GetMapCs();  
            foreach (KeyValuePair<int, string> kvp in iDict)  
            {  
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::set contents:");  
            ICollection<double> iCollDouble = theClass.GetSetCs();  
            foreach (double d in iCollDouble)  
            {  
                Console.WriteLine(d);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::vector contents:");  
            ICollection<int> iCollInt = theClass.GetVectorCs();  
            foreach (int i in iCollInt)  
            {  
                Console.WriteLine(i);  
            }  
            Console.WriteLine();  
  
            return 0;  
        }  
    }  
}  
```  
  
### <a name="output"></a>Výstup  
  
```  
cliext::deque contents:  
a  
b  
  
cliext::list contents:  
3.14159  
2.71828  
  
cliext::map contents:  
0 Hello  
1 World  
  
cliext::set contents:  
2.71828  
3.14159  
  
cliext::vector contents:  
10  
20  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)