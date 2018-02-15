---
title: "Třída Platform::Object | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
dev_langs:
- C++
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa882c22aab21fe82abb2884305bc314997f36a4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformobject-class"></a>Platform::Object – třída
Poskytuje společné chování pro ref třídy a struktury ref v prostředí Windows Runtime aplikace. Všechny ref třídy a instance ref struktura jsou implicitně převést na Platform::Object ^ a jeho virtuální metody ToString můžete přepsat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class Object : Object  
```  
  
### <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Object::Object](#ctor)|Inicializuje novou instanci třídy objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Object::Equals](#equals)|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.|  
|[Object::GetHashCode](#gethashcode)|Vrátí kód hash této instance.|  
|[Object::ReferenceEquals](#referenceequals)|Určuje, zda jsou zadané instance objektu stejné instanci.|  
|[ToString](#tostring)|Vrací řetězec, který představuje aktuální objekt. Je možné přepsat.|  
|[GETTYPE –](#gettype)|Získá [Platform::Type](../cppcx/platform-type-class.md) , který popisuje aktuální instance.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Object`  
  
 `Object`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** vccorlib.h  
  
 **Namespace:** platformy  

  
## <a name="equals"></a> Object::Equals – metoda
Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
bool Equals(  
    Object^ obj  
)  
```  
  
### <a name="parameters"></a>Parametry  
 obj  
 Objekt k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud jsou objekty stejné, jinak `false`.  
  


## <a name="gethashcode"></a>  Object::GetHashCode – metoda
Vrátí `IUnknown`* hodnotu identity pro tuto instanci, pokud je objekt COM nebo hodnotu hash počítaný, pokud není objekt COM.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číselnou hodnotu, která jednoznačně identifikuje tento objekt.  
  
### <a name="remarks"></a>Poznámky  
 GetHashCode můžete použít k vytvoření klíčů pro objekty v rámci služby maps. Hash – kódy, můžete porovnat s použitím [Object::Equals](#equals). Pokud cesta kódu je velmi důležité a `GetHashCode` a `Equals` nejsou dostatečně rychlé, pak můžete rozevírací nabídku do základní vrstvy COM a provést nativní `IUnknown` ukazatel porovnání.  
  


## <a name="gettype"></a>  Object::gettype – metoda
Vrátí [Platform::Type](../cppcx/platform-type-class.md) objekt, který popisuje typ objektu v modulu runtime.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Object::GetType()  
```  

  
### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 A [Platform::Type](../cppcx/platform-type-class.md) objekt, který popisuje runtime typ objektu.  
  
### <a name="remarks"></a>Poznámky  
 Statické [Type::GetTypeCode](../cppcx/platform-type-class.md#gettypecode) můžete použít k získání [Platform::TypeCode výčtu](../cppcx/platform-typecode-enumeration.md) hodnotu, která představuje typ aktuální. Toto je většinou vhodné pro vestavěné typy. Typ kódu pro třídy ref, kromě [Platform::String](../cppcx/platform-string-class.md) je objekt (1).  
  
 [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) třída se používá v rozhraní API systému Windows jako způsob nezávislé na jazyku předávání informací o typu mezi součásti systému Windows a aplikací. T[Platform::Type třída](../cppcx/platform-type-class.md) má operátory pro převod mezi `Type` a `TypeName`.  
  
 Použití [typeid](../windows/typeid-cpp-component-extensions.md) operátor vrátit `Platform::Type` objekt pro název třídy, například při navigaci mezi stránkami XAML:  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
## <a name="see-also"></a>Viz také  
 [Platform::type – třída](../cppcx/platform-type-class.md)   
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)   
 [Type System](../cppcx/type-system-c-cx.md
  
## <a name="ctor"></a>  Object::Object – konstruktor
Inicializuje novou instanci třídy objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:Object()  
```  

## <a name="referenceequals"></a>  Object::ReferenceEquals – metoda
Určuje, zda jsou zadané instance objektu stejné instanci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2)  
```  
  
### <a name="parameters"></a>Parametry  
 obj1  
 První objekt k porovnání.  
  
 obj2  
 Druhý objekt k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud dva objekty jsou stejné. v opačném `false`.  
 
## <a name="tostring"></a>  Metoda Object::ToString (C + +/ CX)
Vrací řetězec, který představuje aktuální objekt.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:  
virtual String^ ToString()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec, který představuje aktuální objekt. Můžete přepsat tuto metodu za účelem zadejte vlastní řetězec zprávu ve vaší ref třídě nebo struktuře:  
  
```cpp  
public ref class Tree sealed  
{  
public:  
    Tree(){}  
    virtual Platform::String^ ToString() override  
    {  
      return "I’m a Tree";  
    };  
};  
```  
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)