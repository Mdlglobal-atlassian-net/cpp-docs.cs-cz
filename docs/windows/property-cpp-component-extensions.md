---
title: vlastnost (rozšíření komponent C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- property_cpp
- property
dev_langs:
- C++
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b763131fe91e2df2385f2c06bcba8bc759d695a1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882703"
---
# <a name="property--c-component-extensions"></a>property (rozšíření komponent C++)
Deklaruje *vlastnost*, což je členské funkce, který se chová a je přístupný jako člena dat nebo k elementu pole.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 Je možné deklarovat jeden z následujících typů vlastností.  
  
 *jednoduché vlastnosti*  
 Ve výchozím nastavení vytvoří *nastavení přístupového objektu* který přiřazuje hodnotu vlastnosti *načtení přístupového objektu* , načte hodnotu vlastnosti a generované kompilátorem privátní data člena, který obsahuje hodnoty vlastnosti.  
  
 *Vlastnost bloku*  
 Použijte k vytvoření uživatelem definované get a nastavení přístupových objektů. Pokud je vlastnost pro čtení a zápis get a přístupových objektů sady jsou definované, pokud jenom přistupující objekt get je definována jen pro čtení a jen pro zápis, pokud, jen je definována přistupující objekt set.  
  
 Je potřeba explicitně deklarovat datový člen obsahuje hodnotu vlastnosti.  
  
 *indexované vlastnosti*  
 Vlastnost blok, který můžete použít k získání a nastavení hodnotu vlastnosti, která je zadána jedna nebo více indexů.  
  
 Můžete vytvořit indexované vlastnosti, která má buď název uživatelem definované vlastnosti nebo *výchozí* název vlastnosti. Název vlastnosti výchozí index je název třídy, ve kterém je definovaný vlastnost. Deklarace vlastnosti výchozí, zadejte `default` – klíčové slovo místo názvu vlastnosti.  
  
 Je potřeba explicitně deklarovat datový člen obsahuje hodnotu vlastnosti. Datový člen indexované vlastnosti, je obvykle pole nebo kolekce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property type property_name;

property type property_name { 
   access-modifier type get() inheritance-modifier {property_body}; 
   access-modifier void set(type value) inheritance-modifier {property_body};
} 

property type property_name[index_list] { 
   access-modifier type get(index_list) inheritance-modifier {property_body}; 
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
} 

property type default[index_list] { 
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}  
```  
  
### <a name="parameters"></a>Parametry  
 `type`  
 Datový typ hodnoty vlastnosti a proto samotné vlastnosti.  
  
 `property_name`  
 Název vlastnosti  
  
 `access-modifier`  
 Kvalifikátor k přístupu. Jsou platné kvalifikátory `static` a `virtual`.  
  
 Zjištění nebo nemusí odsouhlasení sadu přístupových objektů `virtual` kvalifikátor, ale musí souhlasit s na `static` kvalifikátor.  
  
 `inheritance-modifier`  
 Dědičnosti kvalifikátor. Jsou platné kvalifikátory `abstract` a `sealed`.  
  
 `index_list`  
 Čárkami oddělený seznam jednoho nebo více indexů. Každý index se skládá z typ indexu a volitelné identifikátor, který lze použít v těle metoda vlastnost.  
  
 `value`  
 Hodnota k přiřadit k vlastnosti v operace nastavení nebo načtení v operaci get.  
  
 `property_body`  
 Text metoda vlastnost přistupujícího objektu sady nebo get. `property_body` Můžete použít `index_list` pro přístup k základní datový člen vlastnost, nebo jako parametry v uživatelem definované zpracování.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Další informace najdete v tématu [vlastnosti (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh755807.aspx).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Syntaxe**  
  
```cpp  
modifier property type property_name;

modifier property type property_name {
   modifier void set(type);
   modifier type get();
}
modifier property type property_name[index-list, value] {
   modifier void set(index-list, value);
   modifier type get(index-list);

modifier property type default[index];
}  
```  
  
 **Parametry**  
  
 *Modifikátor*  
 Modifikátor, který lze použít na deklarace vlastnosti nebo metody přistupující objekt get/set. Možné hodnoty jsou `static` a `virtual`.  
  
 *Typ*  
 Typ hodnoty, která je reprezentována vlastnost.  
  
 *%{Property_Name/*  
 Parametry pro metodu vyvolat; podpis delegáta, se musí shodovat.  
  
 *index_list*  
 Čárkami oddělený seznam jednoho nebo více indexů, zadaný v hranaté závorky (operátor dolního indexu, ([])). Pro každý index zadejte v těle metoda vlastnost typu a volitelně identifikátor, který lze použít.  
  
 **Poznámky**  
  
 První příklad ukazuje syntaxi *jednoduché vlastnost*, které obě implicitně deklaruje `set` a `get` metoda. Kompilátor automaticky vytvoří soukromé pole k uložení hodnoty vlastnosti.  
  
 Druhý příklad ukazuje syntaxi *vlastnost bloku*, které obě explicitně deklaruje `set` a `get` metoda.  
  
 Třetí příklad syntaxe ukazuje zákazník definovaný *index – vlastnost*. Vlastnost index přebírá parametry kromě hodnota, která má nelze nastavit ani načíst. Je nutné zadat název vlastnosti. Na rozdíl od jednoduché vlastnosti `set` nebo `get` metody vlastnost index musí být explicitně definován a je nutné zadat název vlastnosti.  
  
 Čtvrtý příklad ukazuje syntaxi *výchozí* vlastnost, která poskytuje přístup jako pole pro instanci typu. Klíčové slovo, `default`, slouží pouze k určení výchozí vlastnost. Název výchozí vlastnosti je název typu, ve kterém je definovaný vlastnost.  
  
 `property` – Klíčové slovo může zobrazit ve třídě, rozhraní nebo typ hodnoty. Vlastnost může mít funkci get (jen pro čtení), funkci set (jen zápisu) nebo obě (pro čtení a zápis).  
  
 Název vlastnosti nesmí shodovat s názvem spravované třídy, který jej obsahuje. Návratový typ funkce getter musí odpovídat typu poslední parametru odpovídající funkce pro nastavení.  
  
 Na kód klienta vlastnost má vzhled člena obyčejnou dat a může být číst nebo z pomocí stejnou syntaxi jako datový člen.  
  
 Zjištění a metody set nemusí odsouhlasení `virtual` modifikátor.  
  
 Usnadnění operace get a set – metoda se může lišit.  
  
 Definice metoda property se může zobrazit mimo tělo třídy, stejně jako obyčejnou metoda.  
  
 Zjištění a metodu set pro vlastnost dohodnou **statické** modifikátor.  
  
 Vlastnost je skalární pokud jeho get a metody set podle následujícího popisu:  
  
-   Metoda get nemá žádné parametry a návratový typ má `T`.  
  
-   Metody set má parametr typu `T`a návratový typ **void**.  
  
 Musí existovat pouze jedna skalární vlastnost deklarované v oboru se stejným identifikátorem. Skalární vlastnosti nemohou být přetíženy.  
  
 Pokud je deklarovaná vlastnost data člena, kompilátor vloží datový člen – někdy označuje jako "zálohování úložiště" – v třídě. Název člena dat je však ve tvaru, tak, aby člena ve zdroji nelze odkazovat, jako by šlo člena skutečná data obsahující třídy. Použijte ildasm.exe zobrazení metadat pro váš typ a zobrazí název generované kompilátorem pro vlastnosti záložnímu úložišti.  
  
 Různé usnadnění je povolena pro přístupových metod v bloku vlastnost.  To znamená metoda sada může být veřejné a metody get může být privátní.  Je však chybu pro metodu přistupujícího objektu tak, aby měl méně omezující usnadnění, než jaký je v prohlášení o samotné vlastnosti.  
  
 `property` je kontextová – klíčové slovo.  Další informace najdete v tématu [klíčová slova Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 Následující příklad ukazuje deklarace a používání dat člena vlastnosti a vlastnosti bloku.  Také ukazuje, že přistupujícího objektu vlastnosti lze definovat mimo třídy.  
  
```  
// mcppv2_property.cpp  
// compile with: /clr  
using namespace System;  
public ref class C {  
   int MyInt;  
public:  
  
   // property data member  
   property String ^ Simple_Property;  
  
   // property block  
   property int Property_Block {  
  
      int get();  
  
      void set(int value) {  
         MyInt = value;  
      }  
   }  
};  
  
int C::Property_Block::get() {  
   return MyInt;  
}  
  
int main() {  
   C ^ MyC = gcnew C();  
   MyC->Simple_Property = "test";  
   Console::WriteLine(MyC->Simple_Property);  
  
   MyC->Property_Block = 21;  
   Console::WriteLine(MyC->Property_Block);  
}  
```  
  
 **Output**  
  
```Output  
test  
  
21  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)