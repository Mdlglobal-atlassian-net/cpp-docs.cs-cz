---
title: "Messages – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
dev_langs: C++
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d60a1ba5ac8acbb6fbaf9e5b7e922a1f373f9293
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="messages-class"></a>messages – třída
Třída šablony popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí k načítání lokalizovaných zpráv z katalogu internacionalizovaných zpráv pro dané národní prostředí.  
  
 Je-li třída zpráv aktuálně implementována, nejsou k dispozici žádné zprávy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class CharType>  
class messages : public messages_base;
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ používaný v rámci programu ke kódování znaků v národním prostředí.  
  
## <a name="remarks"></a>Poznámky  
 Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty **id.**  
  
 Tato omezující vlastnost v podstatě otevře katalog zpráv definovaný v základní třídě messages_base, načte požadované informace a katalog zavře.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[zprávy](#messages)|Funkce konstruktoru omezující vlastnosti zpráv.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type –](#char_type)|Typ znaku, který je používán pro zobrazení zpráv.|  
|[STRING_TYPE](#string_type)|Typ, který popisuje řetězec typu `basic_string` obsahující znaky typu `CharType`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[Zavřete](#close)|Zavře katalog zpráv.|  
|[do_close –](#do_close)|Virtuální funkce volaná k zavření katalogu zpráv.|  
|[do_get –](#do_get)|Virtuální funkce volaná k načtení katalogu zpráv.|  
|[do_open –](#do_open)|Virtuální funkce volaná k otevření katalogu zpráv.|  
|[GET](#get)|Načte katalog zpráv.|  
|[Otevřete](#open)|Otevře katalog zpráv.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
##  <a name="char_type"></a>Messages::char_type  
 Typ znaku, který je používán pro zobrazení zpráv.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **CharType**.  
  
##  <a name="close"></a>Messages::Close  
 Zavře katalog zpráv.  
  
```
void close(catalog _Catval) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Catval`  
 Katalog bude uzavřen.  
  
### <a name="remarks"></a>Poznámky  
 Volání členských funkcí [do_close –](#do_close)(_ *Catval*).  
  
##  <a name="do_close"></a>Messages::do_close  
 Virtuální funkce volaná k zavření katalogu zpráv.  
  
```
virtual void do_close(catalog _Catval) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Catval`  
 Katalog bude uzavřen.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen funkce zavře katalogu zpráva `_Catval`, který byl otevřen starší voláním [do_open –](#do_open).  
  
 *_Catval* musí být získána z dříve otevřen katalog, který není uzavřený.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [zavřete](#close), který volá `do_close`.  
  
##  <a name="do_get"></a>Messages::do_get  
 Virtuální funkce volaná k načtení katalogu zpráv.  
  
```
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Catval`  
 Hodnota identifikace zadání katalogu zpráva má proběhnout.  
  
 `_Set`  
 První identifikovat používaná k nalezení zprávu v katalogu zprávy.  
  
 `_Message`  
 Druhý identifikovat používaná k nalezení zprávu v katalogu zprávy.  
  
 `_Dfault`  
 Řetězec, který se má vrátit při selhání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kopii `_Dfault` při selhání. V opačném případě vrátí kopii pořadí zadané zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Funkce chráněného člena se pokusí získat sekvenci zpráv z katalogu zpráva `_Catval`. Může být použití `_Set`, `_Message`, a `_Dfault` za tím účelem.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [získat](#get), který volá `do_get`.  
  
##  <a name="do_open"></a>Messages::do_open  
 Virtuální funkce volaná k otevření katalogu zpráv.  
  
```
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Catname`  
 Název katalogu je vyhledán.  
  
 `_Loc`  
 Národní prostředí vyhledána v katalogu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu, která porovná menší než nula. na selhání. Jinak, vrácené hodnoty mohou být použity jako první argument na novější volání [získat](#get).  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen funkce pokusí otevřít zpráva katalogu, jehož název je `_Catname`. Může být použití národní prostředí `_Loc` přitom  
  
 Návratová hodnota má být použit jako argument na novější volání [zavřete](#close).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [otevřete](#open), který volá `do_open`.  
  
##  <a name="get"></a>Messages::Get  
 Načte katalog zpráv.  
  
```
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Catval`  
 Hodnota identifikace zadání katalogu zpráva má proběhnout.  
  
 `_Set`  
 První identifikovat používaná k nalezení zprávu v katalogu zprávy.  
  
 `_Message`  
 Druhý identifikovat používaná k nalezení zprávu v katalogu zprávy.  
  
 `_Dfault`  
 Řetězec, který se má vrátit při selhání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kopii `_Dfault` při selhání. V opačném případě vrátí kopii pořadí zadané zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_get –](#do_get)( `_Catval`, `_Set`, `_Message`, `_Dfault`).  
  
##  <a name="messages"></a>Messages::Messages  
 Funkce konstruktoru omezující vlastnosti zpráv.  
  
```
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `_Refs`  
 Celočíselná hodnota určuje typ správy paměti pro objekt.  
  
 `_Locname`  
 Název národního prostředí.  
  
### <a name="remarks"></a>Poznámky  
 Možné hodnoty `_Refs` parametrů a jejich významu jsou:  
  
-   0: doba života objektu spravuje národní prostředí, které je obsahují.  
  
-   1: doba života objektu, se musí ručně spravovat.  
  
-   \>1: tyto hodnoty nejsou definovány.  
  
 Žádné přímé příklady je možné, protože je chráněn destruktoru.  
  
 Konstruktor inicializuje jeho základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)( `_Refs`).  
  
##  <a name="open"></a>Messages::Open  
 Otevře katalog zpráv.  
  
```
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Catname`  
 Název katalogu je vyhledán.  
  
 `_Loc`  
 Národní prostředí vyhledána v katalogu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu, která porovná menší než nula. na selhání. Jinak, vrácené hodnoty mohou být použity jako první argument na novější volání [získat](#get).  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_open –](#do_open)( `_Catname`, `_Loc`).  
  
##  <a name="string_type"></a>Messages::STRING_TYPE  
 Typ, který popisuje řetězec typu `basic_string` obsahující znaky typu **CharType**.  
  
```
typedef basic_string<CharType, Traits, Allocator> string_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [basic_string](../standard-library/basic-string-class.md) jejichž objekty může ukládat kopie zprávy pořadí.  
  
## <a name="see-also"></a>Viz také  
 [\<národní prostředí >](../standard-library/locale.md)   
 [messages_base – třída](../standard-library/messages-base-class.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


