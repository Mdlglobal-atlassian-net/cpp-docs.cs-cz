---
title: Pole (rozšíření komponent C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
- declaring arrays, about declaring arrays
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 58ba6d598223e63f5b28adcaedad653ffc6f386a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645565"
---
# <a name="arrays-c-component-extensions"></a>Pole (přípony komponent C++)
`Platform::Array<T>` Typu v jazyce C + +/ CX nebo **pole** – klíčové slovo v jazyce C + +/ CLI, deklaruje pole určeného typu a počáteční hodnota.  
  
## <a name="all-platforms"></a>Všechny platformy  
 Pole musí být deklarován pomocí modifikátoru popisovač objektu (^) po pravé ostré závorky (>) v deklaraci.  
 Počet prvků pole, které není součástí typu. Jednu proměnnou pole mohou odkazovat na pole různých velikostí.  
  
 Na rozdíl od standardní C++ vytváření dolních indexů není synonymum pro aritmetika ukazatele a není komutativní.  
  
 Další informace o polích naleznete v tématu:  
  
-   [Postupy: Používání polí v jazyce C++/CLI](../dotnet/how-to-use-arrays-in-cpp-cli.md)  
    
-   [Seznamy argumentů s proměnnou délkou (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Pole jsou členy `Platform` oboru názvů. Pole může být jenom jednorozměrné.  
  
### <a name="syntax"></a>Syntaxe  
  
 První příklad syntaxe používá **ref nové** agregační – klíčové slovo pro přidělení matici. Druhý příklad deklaruje místního pole.  
  
```cpp  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]  
  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *Kvalifikátory* [volitelný]  
 Jeden nebo více těchto specifikátorů třídy úložiště: [proměnlivé](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [statické](../cpp/static-members-cpp.md).  
  
 *Typ pole*  
 Typ proměnné pole. Platné typy jsou třídy Windows Runtime a základní typy, referenční třídy a struktury, hodnota třídy a struktury a nativními ukazateli (`type*`).  
  
 *pořadí* [volitelný]  
 Počet rozměrů pole. Musí být 1.  
  
 *identifikátor*  
 Název proměnné pole.  
  
 *typ inicializace*  
 Typ hodnoty, které inicializovat pole. Obvykle *typ pole* a *typ inicializace* jsou stejného typu. Však mohou být typy lišit, když existuje převod z *typ inicializace* k *typ pole*– například pokud *typ inicializace* je odvozen z *typ pole*.  
  
 *inicializační seznam* [volitelný]  
 Čárkami oddělený seznam hodnot ve složených závorkách, které inicializaci prvků pole. Například pokud *řazení seznamu velikost* byly `(3)`, který deklaruje jednorozměrné pole prvků 3 *inicializačního seznamu* může být `{1,2,3}`.  
  
### <a name="remarks"></a>Poznámky  
  
 V době kompilace může zjistit, zda je typ pole s počítáním referencí s `__is_ref_array(type)`. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/ZW`  
  
### <a name="examples"></a>Příklady  
 Následující příklad vytvoří jednorozměrné pole, která má 100 elementů.  
  
```cpp  
// cwr_array.cpp  
// compile with: /ZW  
using namespace Platform;  
ref class MyClass {};  
int main() {  
   // one-dimensional array  
   Array<MyClass^>^ My1DArray = ref new Array<MyClass^>(100);  
   My1DArray[99] = ref new MyClass();  
}  
```  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
  
### <a name="syntax"></a>Syntaxe  
  
 První příklad syntaxe používá **gcnew** – klíčové slovo pro přidělení matici. Druhý příklad deklaruje místního pole.  
  
```cpp  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]  
  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *Kvalifikátory* [volitelný]  
 Jeden nebo více těchto specifikátorů třídy úložiště: [proměnlivé](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [statické](../cpp/static-members-cpp.md).  
  
 *Typ pole*  
 Typ proměnné pole. Platné typy jsou třídy Windows Runtime a základní typy, referenční třídy a struktury, hodnota třídy a struktury, nativními ukazateli (`type*`) a nativní typy POD (obyčejná stará data).  
  
 *pořadí* [volitelný]  
 Počet rozměrů pole. Výchozí hodnota je 1; maximální počet je 32. Každé dimenze pole je pole.  
  
 *identifikátor*  
 Název proměnné pole.  
  
 *typ inicializace*  
 Typ hodnoty, které inicializovat pole. Obvykle *typ pole* a *typ inicializace* jsou stejného typu. Však mohou být typy lišit, když existuje převod z *typ inicializace* k *typ pole*– například pokud *typ inicializace* je odvozen z *typ pole*.  
  
 *pořadí seznamu velikost*  
 Čárkami oddělený seznam velikosti jednotlivých rozměrů pole. Případně pokud *inicializačního seznamu* parametr zadán, kompilátor může odvodit velikost každého rozměru a *řazení seznamu velikost* lze vynechat. 
  
 *inicializační seznam* [volitelný]  
 Čárkami oddělený seznam hodnot ve složených závorkách, které inicializaci prvků pole. Nebo vnořený seznam oddělený čárkami *inicializačního seznamu* položky, které inicializaci prvků v vícerozměrné pole.  
  
 Například pokud *řazení seznamu velikost* byly `(3)`, který deklaruje jednorozměrné pole prvků 3 *inicializačního seznamu* může být `{1,2,3}`. Pokud *řazení seznamu velikost* byly `(3,2,4)`, který deklaruje třídimenzionální pole prvků 3 v prvním rozměru, 2 prvky za sekundu a 4 prvky v třetí, *inicializačního seznamu* může být `{{1,2,3},{0,0},{-5,10,-21,99}}`.)  
  
### <a name="remarks"></a>Poznámky  
  
 **pole** probíhá [Platform, default a cli obory názvů](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) oboru názvů.  
  
 Podobně jako standardní C++ indexy pole jsou počítány od nuly a pole je indexované pomocí hranatých závorek ([]). Na rozdíl od standardní C++ jsou uvedeny indexy vícerozměrné pole v seznamu indexů pro jednotlivé rozměry namísto sadu operátorů hranatých závorek ([]) pro jednotlivé rozměry. Například *identifikátor*[*index1*, *index2*] místo *identifikátor*[*index1*] [ *index2*].  
  
 Dědí všechny spravovaných polí `System::Array`. Všechny metody nebo vlastnosti z `System::Array` lze použít přímo k proměnné pole.  
  
 Když přidělíte pole, jehož typ prvku je ukazatel-spravovanou třídu prvky jsou inicializovány 0.  
  
 Když přidělíte pole, jehož typ prvku je typ hodnoty `V`, výchozí konstruktor pro `V` se aplikuje na každý prvek pole. Další informace najdete v tématu [rozhraní .NET Framework – ekvivalenty nativních typů C++ (C + +/ CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md).  
  
 V době kompilace, můžete zjistit, zda je typ common language runtime (CLR) pole `__is_ref_array(type)`. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/clr`  
  
### <a name="examples"></a>Příklady  
 Následující příklad vytvoří jednorozměrné pole, která má 100 elementů a trojrozměrného pole, která má 3 elementů v prvním rozměru, 5 elementů do druhého a 6 prvků v třetí.  
  
```cpp  
// clr_array.cpp  
// compile with: /clr  
ref class MyClass {};  
int main() {  
   // one-dimensional array  
   array<MyClass ^> ^ My1DArray = gcnew array<MyClass ^>(100);  
   My1DArray[99] = gcnew MyClass();  
  
   // three-dimensional array  
   array<MyClass ^, 3> ^ My3DArray = gcnew array<MyClass ^, 3>(3, 5, 6);  
   My3DArray[0,0,0] = gcnew MyClass();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)