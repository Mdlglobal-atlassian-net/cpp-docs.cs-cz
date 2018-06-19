---
title: Třída Platform::String | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7a18b1a8ced533389b5938d44a73589336f717f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094823"
---
# <a name="platformstring-class"></a>Platform::String – třída
Představuje kolekci sekvenční znaky Unicode, která se používá k reprezentování text. Další informace a příklady naleznete v tématu [řetězce](../cppcx/strings-c-cx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
public ref class String sealed : Object,  
    IDisposable,  
    IEquatable,  
    IPrintable  
```  
  
## <a name="iterators"></a>Iterátory  
 Dvě iterator funkce, které nejsou členy třídy String, lze použít s `std::for_each` funkce šablony výčet znaky v řetězci objektu.  
  
|Člen|Popis|  
|------------|-----------------|  
|`const char16* begin(String^ s)`|Vrátí ukazatel na začátek zadaný objekt řetězce.|  
|`const char16* end(String^ s)`|Vrátí ukazatel za koncem zadaný objekt řetězce.|  
  
### <a name="members"></a>Členové  
 Řetězec třídy dědí z objektu a rozhraní IDisposable IEquatable a IPrintable.  
  
 Třída řetězec má také následující typy členů.  
  
 **Konstruktory**  
  
|Člen|Popis|  
|------------|-----------------|  
|[String::String](#ctor)|Inicializuje novou instanci třídy String.|  
  
 **Metody**  
  
 Třída řetězec dědí z metody Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() a ToString() [Platform::Object třída](../cppcx/platform-object-class.md). Řetězec má také následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[String::begin](#begin)|Vrací ukazatel na začátku aktuálního řetězce.|  
|[String::CompareOrdinal](#compareordinal)|Porovná dva `String` objekty vyhodnocením číselné hodnoty odpovídající znaků v dvě řetězcové hodnoty reprezentována objekty.|  
|[String::concat](#concat)|Zřetězí hodnoty dvou řetězcových objektů.|  
|[String::data](#data)|Vrací ukazatel na začátku aktuálního řetězce.|  
|[String::dispose](#dispose)|Uvolní nebo uvolní prostředky.|  
|[String::end](#end)|Vrátí ukazatel za koncem aktuálního řetězce.|  
|[String::Equals](#equals)|Určuje, zda zadaný objekt rovná aktuálnímu objektu.|  
|[String::GetHashCode](#gethashcode)|Vrátí kód hash této instance.|  
|[String::IsEmpty](#isempty)|Určuje, zda aktuální objekt řetězce je prázdný.|  
|[String::IsFastPass](#isfastpass)|Určuje, zda se účastní aktuálního řetězce je objekt *rychlé průchodu* operaci. V rychlého předat operace, počítání odkaz je pozastaveno.|  
|[String::length](#length)|Načte délka aktuální objekt řetězce.|  
|[String::ToString](#tostring)|Vrátí objekt řetězec, jehož hodnota je stejná jako aktuální řetězec.|  
  
 **Operátory**  
  
 Třída řetězec má následující operátory.  
  
|Člen|Popis|  
|------------|-----------------|  
|[String::Operator == – operátor](#operator-equality)|Určuje, zda dva objekty zadaný řetězec mají stejnou hodnotu.|  
|[Operator + – operátor](#operator-plus)|Zřetězí dva objekty řetězec do nového objektu řetězce.|  
|[String::Operator > – operátor](#operator-greater-than)|Určuje, zda je hodnota jeden řetězec objekt větší než hodnota druhý objekt řetězce.|  
|[String::Operator > = – operátor](#operator-greater-than-or-equals)|Určuje, zda je hodnota jeden řetězec objekt větší než nebo rovna hodnotě druhý objekt řetězce.|  
|[String::Operator! = – operátor](#operator-inequality)|Určuje, zda dva objekty zadaný řetězec mají různé hodnoty.|  
|[String::Operator < – operátor](#operator-less-than)|Určuje, zda hodnota jednoho objektu řetězce je menší než hodnota druhý objekt řetězce.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Záhlaví** vccorlib.h (zahrnuté ve výchozím nastavení)  

 
## <a name="begin"></a>  String::begin – metoda
Vrací ukazatel na začátku aktuálního řetězce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
char16* Begin()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na začátku aktuálního řetězce.  
  
## <a name="compareordinal"></a>  String::CompareOrdinal – metoda
Porovná dva `String` objekty vyhodnocením číselné hodnoty odpovídající znaků v dvě řetězcové hodnoty reprezentována objekty.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
int CompareOrdinal(  
           String^ str1,   
           String^ str2)  
  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První řetězec objektu.  
  
 `str2`  
 Druhý objekt řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo, které označuje lexikální vztah mezi dvěma comparands. Následující tabulka uvádí možné vrácené hodnoty.  
  
|Hodnota|Podmínka|  
|-----------|---------------|  
|-1|`str1` je menší než `str2`.|  
|0|`str1` se rovná `str2`.|  
|1|`str1` je větší než `str2`.|  
  


## <a name="concat"></a>  String::concat – metoda
Zřetězí hodnoty dvou řetězcových objektů.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
String^ Concat( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První řetězec objekt, nebo `null`.  
  
 `str2`  
 Druhý objekt řetězce nebo `null`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nový řetězec ^ objekt, jehož hodnota je zřetězení hodnoty z `str1` a `str2`.  
  
 Pokud `str1` je `null` a `str2` není, `str1` je vrácen. Pokud `str2` je `null` a `str1` není, `str2` je vrácen. Pokud `str1` a `str2` jsou oba `null`, prázdný řetězec (L"") je vrácen.  
  


## <a name="data"></a>  String::data – metoda
Vrátí ukazatel na začátek vyrovnávací paměť dat objektu jako stylu jazyka C pole `char16` (`wchar_t`) elementy.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
const char16* Data()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na začátku `const char16` pole znaků Unicode (`char16` je typedef pro `wchar_t`).  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete převést z `Platform::String^` k `wchar_t*`. Když `String` opuštění rozsahu, ukazatele dat už záruku, že byla platná. K ukládání dat nad rámec životnost původní `String` objektu, použijte [wcscpy_s –](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) ke kopírování pole do paměti, které jste přidělili sami.  
  


## <a name="dispose"></a>  String::Dispose – metoda
Uvolní nebo uvolní prostředky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
virtual override void Dispose()  
```  

## <a name="end"></a>  String::end – metoda
Vrátí ukazatel za koncem aktuálního řetězce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
char16* End()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na za koncem aktuálního řetězce.  
  
### <a name="remarks"></a>Poznámky  
 End() vrátí Begin() + délka.  
  


## <a name="equals"></a>  String::Equals – metoda
Určuje, zda zadaný řetězec má stejnou hodnotu jako aktuální objekt.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
bool String::Equals(Object^ str);  
  
bool String::Equals(String^ str);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Objekt k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `str` je stejný jako aktuální objekt, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je ekvivalentní [String::CompareOrdinal](#compareordinal). V první přetížení se očekává `str` lze parametr převést na řetězec ^ objektu.  
  


## <a name="gethashcode"></a>  String::GetHashCode – metoda
Vrátí kód hash této instance.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
virtual override int GetHashCode()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kód hash této instance  
  


## <a name="isempty"></a>  String::IsEmpty – metoda
Určuje, zda aktuální objekt řetězce je prázdný.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
bool IsEmpty()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je aktuální objekt řetězec `null` nebo prázdný řetězec (L""), jinak hodnota `false`.  
  


## <a name="isfastpass"></a>  String::IsFastPass – metoda
Určuje, zda se účastní aktuálního řetězce je objekt *rychlé průchodu* operaci. V rychlého předat operace, počítání odkaz je pozastaveno.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
bool IsFastPass();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud se aktuální objekt řetězec fast minulosti; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Ve volání funkce, kde objekt počítá odkaz je parametr, a volaná funkce četl pouze tento objekt můžete kompilátor bezpečně pozastavit počítání odkazů a zlepšit výkon volání. Není co užitečné, že váš kód můžete provádět s touto vlastností. Systém zpracovává všechny podrobnosti.  
  


## <a name="length"></a>  String::length – metoda
Načte počet znaků v aktuální objekt řetězce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
unsigned int Length()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků v aktuální objekt řetězce.  
  
### <a name="remarks"></a>Poznámky  
 Délka řetězce se žádné znaky je nula. Délka následující řetězec je 5:  
  
```    
String^ str = "Hello";  
int len = str->Length(); //len = 5  
```  
  
 Znak poli vráceném [String::Data](#data) má jeden další znak, což je ukončující hodnotu NULL nebo '\0'. Tento znak je také dva bajty.  
  


## <a name="operator-plus"></a>  String::Operator + – operátor
Zřetězí dvě [řetězec](../cppcx/platform-string-class.md) objektů do nové [řetězec](../cppcx/platform-string-class.md) objektu.
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
bool String::operator+( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První `String` objektu.  
  
 `str2`  
 Druhý `String` objekt, jejichž obsah se připojí k `str1`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `str1` rovná `str2`, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor vytvoří `String^` objekt, který obsahuje data z dva operandy. Používejte pro usnadnění práce při extrémně výkon není důležité. Několik volání "`+`" ve funkci nejspíš bude patrné, ale pokud manipulaci rozsáhlé objekty nebo textová data ve smyčce úzkou, použijte standardní C++ mechanismy a typy.  
  
##  <a name="operator-equality"></a> String::Operator == – operátor
Určuje, zda dva objekty zadaný řetězec mají stejnou hodnotu text.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
bool String::operator==( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První řetězec objekt k porovnání.  
  
 `str2`  
 Druhý řetězec objekt k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud obsah `str1` rovná `str2`, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor je ekvivalentní [String::CompareOrdinal](#compareordinal).  
  


##  <a name="operator-greater-than"></a>  String::Operator&gt; 
Určuje, zda je hodnota jeden řetězec objekt větší než hodnota druhý objekt řetězce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
bool String::operator>( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První řetězec objektu.  
  
 `str2`  
 Druhý objekt řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud hodnota `str1` je větší než hodnota `str2`, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor je ekvivalentní volání explicitně [String::CompareOrdinal](#compareordinal) a získávání výsledku větší než nula.  
  


## <a name="operator-greater-than-or-equals"></a> String::Operator&gt;= 
Určuje, zda je hodnota jeden řetězec objekt větší než nebo rovna hodnotě druhý objekt řetězce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
bool String::operator>=( String^ str1, String^ str2) 
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První řetězec objektu.  
  
 `str2`  
 Druhý objekt řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud hodnota `str1` je větší než nebo rovna hodnotě `str2`, jinak hodnota `false`.  
  


## <a name="operator-inequality"></a> String::Operator! = 
Určuje, zda dva objekty zadaný řetězec mají různé hodnoty.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
bool String::operator!=( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První řetězec objekt k porovnání.  
  
 `str2`  
 Druhý řetězec objekt k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `str1` se nerovná `str2`, jinak hodnota `false`.   


## <a name="operator-less-than"></a> String::Operator&lt; 
Určuje, zda hodnota jednoho objektu řetězce je menší než hodnota druhý objekt řetězce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
bool String::operator<( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První řetězec objektu.  
  
 `str2`  
 Druhý objekt řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud hodnota `str1` je menší než hodnota `str2`, jinak hodnota `false`.  
  
## <a name="ctor"></a> String::String – konstruktor
Inicializuje novou instanci třídy String kopii dat vstupní řetězec.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
String();    
String(char16* s)  
String(char16* s, unsigned int n)  
```  
  
### <a name="parameters"></a>Parametry  
 `s`  
 Řada široké znaky, které Inicializuje řetězec. char16  
  
 `n`  
 Číslo, které určuje délku řetězce.  
  
### <a name="remarks"></a>Poznámky  
 Pokud výkon je velmi důležité a řídí životnost zdrojový řetězec, můžete použít [Platform::StringReference](../cppcx/platform-stringreference-class.md) místo řetězec.  
### <a name="example"></a>Příklad  
  
```cpp  
String^ s = L"Hello!";  
```  
  
## <a name="tostring"></a> String::ToString
Vrátí objekt řetězec, jehož hodnota je stejná jako aktuální řetězec.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
String^ String::ToString()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt String, jehož hodnota je stejná jako aktuální řetězec.  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)