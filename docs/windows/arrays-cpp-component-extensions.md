---
title: "Pole (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- cli::array
- details::array
- lang::array
dev_langs: C++
helpviewer_keywords:
- array keyword [C++]
- declaring arrays, about declaring arrays
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
caps.latest.revision: "34"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a2f0f4100344fbb2990e9feeb2b455642852c320
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="arrays-c-component-extensions"></a>Pole (přípony komponent C++)
`Platform::Array<T>` Typ v jazyce C + +/ CX, nebo `array` – klíčové slovo v jazyce C + +/ CLI, deklaruje pole zadaného typu a počáteční hodnota.  
  
## <a name="all-platforms"></a>Všechny platformy  
 Pole musí být deklarován pomocí modifikátoru popisovač objektu (^) po ukončovací lomená závorka (>) v deklaraci.  
 Počet elementů pole není součástí typu. Jednu proměnnou pole mohou odkazovat na pole různých velikostí.  
  
 Na rozdíl od standardní C++ předplatné není synonymum pro aritmetika ukazatele a není komutativní.  
  
 Další informace o polích najdete v tématu:  
  
-   [Postupy: použití polí v jazyce C + +/ CLI](../dotnet/how-to-use-arrays-in-cpp-cli.md)  
    
-   [Seznam argumentů s proměnnou délkou (...) (C + +/ CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Pole jsou členy `Platform` oboru názvů. Pole může být pouze jednorozměrné.  
  
### <a name="syntax"></a>Syntaxe  
  
 V prvním příkladu syntaxe používá `ref new` agregační – klíčové slovo přidělit pole. V druhém příkladu deklaruje místní pole.  
  
```  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]  
  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *Kvalifikátory* [Nepovinné]  
 Jeden nebo více těchto specifikátory třídy úložiště: [měnitelný](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [statické](../cpp/static-members-cpp.md).  
  
 `array-type`  
 Typ proměnné pole. Platné typy jsou třídy prostředí Windows Runtime a základní typy, ref třídy a struktury, hodnota třídy a struktury a nativními ukazateli (`type*`).  
  
 `rank`[Nepovinné]  
 Počet rozměrů pole. Musí být 1.  
  
 `identifier`  
 Název proměnné pole.  
  
 `initialization-type`  
 Typ hodnoty, které inicializovat pole. Obvykle `array-type` a `initialization-type` jsou stejného typu. Typy však může být různé, pokud je převod z `initialization-type` k `array-type`– například pokud `initialization-type` je odvozený od `array-type`.  
  
 `initialization-list`[Nepovinné]  
 Čárkami oddělený seznam hodnot v složené závorky, které inicializovat elementy pole. Například pokud `rank-size-list` byly `(3)`, který deklaruje jednorozměrné pole 3 elementů `initialization list` může být `{1,2,3}`.  
  
### <a name="remarks"></a>Poznámky  
  
 V době kompilace může zjistit, jestli typ je počítáno odkaz na pole s `__is_ref_array(type)`. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
### <a name="examples"></a>Příklady  
 Následující příklad vytvoří jednorozměrné pole, které má 100 elementy.  
  
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
  
 V prvním příkladu syntaxe používá `gcnew` – klíčové slovo přidělit pole. V druhém příkladu deklaruje místní pole.  
  
```  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]  
  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *Kvalifikátory* [Nepovinné]  
 Jeden nebo více těchto specifikátory třídy úložiště: [měnitelný](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [statické](../cpp/static-members-cpp.md).  
  
 `array-type`  
 Typ proměnné pole. Platné typy jsou třídy prostředí Windows Runtime a základní typy, ref třídy a struktury, hodnota třídy a struktury, nativními ukazateli (`type*`) a nativní typy POD (prostý stará data).  
  
 `rank`[Nepovinné]  
 Počet rozměrů pole. Výchozí hodnota je 1; maximální počet je 32. Každé pole je sám pole.  
  
 `identifier`  
 Název proměnné pole.  
  
 `initialization-type`  
 Typ hodnoty, které inicializovat pole. Obvykle `array-type` a `initialization-type` jsou stejného typu. Typy však může být různé, pokud je převod z `initialization-type` k `array-type`– například pokud `initialization-type` je odvozený od `array-type`.  
  
 `rank-size-list`  
 Čárkami oddělený seznam velikost Každá dimenze v poli. Případně pokud `initialization-list` je zadán parametr, kompilátor lze odvodit velikost Každá dimenze a `rank-size-list` lze vynechat. 
  
 `initialization-list`[Nepovinné]  
 Čárkami oddělený seznam hodnot v složené závorky, které inicializovat elementy pole. Nebo vnořený seznam s položkami oddělenými čárkou *Inicializace seznamu* položky, které inicializovat elementů v vícerozměrné.  
  
 Například pokud `rank-size-list` byly `(3)`, který deklaruje jednorozměrné pole 3 elementů `initialization list` může být `{1,2,3}`. Pokud `rank-size-list` byly `(3,2,4)`, který deklaruje trojrozměrné 3 elementů v první dimenze, 2 prvky za sekundu a 4 elementy do třetího `initialization-list` může být `{{1,2,3},{0,0},{-5,10,-21,99}}`.)  
  
### <a name="remarks"></a>Poznámky  
  
 `array`Probíhá [Platform, default a rozhraní příkazového řádku obory názvů](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) oboru názvů.  
  
 Jako standardní C++ indexy pole jsou od nuly, a pole je dolního indexu pomocí hranaté závorky ([]). Na rozdíl od standardní C++ jsou indexy vícerozměrné určené v seznamu indexy, které pro každý dimenzi namísto sadu operátory hranaté závorky ([]) pro každý dimenzi. Například *identifikátor*[*index1*, *index2*] místo *identifikátor*[*index1*] [ *index2*].  
  
 Dědí všechny spravovaných polí `System::Array`. Žádné metody nebo vlastnosti z `System::Array` lze použít přímo do proměnné pole.  
  
 Pokud přidělíte pole, jehož typ elementu je ukazatel-na třídu spravovaných elementů jsou inicializovat 0.  
  
 Pokud přidělíte pole, jehož typ elementu je typ hodnoty `V`, výchozí konstruktor pro `V` se použije pro každý element pole. Další informace najdete v tématu [rozhraní .NET Framework – ekvivalenty k nativním typy C++ (C + +/ CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md).  
  
 Při kompilaci, můžete zjistit, zda typ je běžné pole language runtime (CLR) s `__is_ref_array(type)`. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 Následující příklad vytvoří jednorozměrné pole, které má 100 elementy a trojrozměrné, který má 3 elementy v první dimenzi, 5 elementy za sekundu a 6 elementů ve třetí.  
  
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
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)