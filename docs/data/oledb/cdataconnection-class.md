---
title: CDataConnection – třída
ms.date: 03/27/2019
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
helpviewer_keywords:
- CDataConnection class
- CDataConnection class, constructor
- Copy method
- Open method
- OpenNewSession method
- BOOL operator
- operator bool
- BOOL operator
- operator bool
- CDataSource& operator
- operator & (CDataSource)
- CDataSource* operator
- operator * (CDataSource)
- operator CSession&
- CSession& operator
- operator CSession*
- CSession* operator
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
ms.openlocfilehash: fe954e218a099fa7956748904a4baa89f741c52f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368619"
---
# <a name="cdataconnection-class"></a>CDataConnection – třída

Spravuje připojení ke zdroji dat.

## <a name="syntax"></a>Syntaxe

```cpp
class CDataConnection
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CDataConnection](#cdataconnection)|Konstruktor Instance inicializuje a inicializuje `CDataConnection` objekt.|
|[Kopírovat](#copy)|Vytvoří kopii existujícího datového připojení.|
|[Otevřít](#open)|Otevře připojení ke zdroji dat pomocí inicializačního řetězce.|
|[OpenNewSession](#opennewsession)|Otevře novou relaci aktuálního připojení.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor BOOL](#op_bool)|Určuje, zda je aktuální relace otevřená či nikoli.|
|[operátor bool](#op_bool_ole)|Určuje, zda je aktuální relace otevřená či nikoli.|
|[operátor CDataSource&](#op_cdata_amp)|Vrátí odkaz na obsažený `CDataSource` objekt.|
|[operátor CDataSource*](#op_cdata_star)|Vrátí ukazatel na obsažený `CDataSource` objekt.|
|[operátor CSession&](#op_csession_amp)|Vrátí odkaz na obsažený `CSession` objekt.|
|[operátor CSession*](#op_csession_star)|Vrátí ukazatel na obsažený `CSession` objekt.|

## <a name="remarks"></a>Poznámky

`CDataConnection`je užitečná třída pro vytváření klientů, protože zapouzdřuje potřebné objekty (zdroj dat a relace) a část práce, kterou je třeba provést při připojování ke zdroji dat

Bez `CDataConnection`, budete muset `CDataSource` vytvořit objekt, volat jeho [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) metoda, pak vytvořit instanci [CSession](../../data/oledb/csession-class.md) objektu, volat `Open`jeho [Open](../../data/oledb/csession-open.md) metoda, pak vytvořit [CCommand](../../data/oledb/ccommand-class.md) objekt a volat jeho * metody.

Pomocí `CDataConnection`aplikace je třeba pouze vytvořit objekt připojení, předat mu inicializační řetězec a potom toto připojení použít k otevření příkazů. Pokud plánujete používat připojení k databázi opakovaně, je vhodné ponechat připojení `CDataConnection` otevřené a poskytuje pohodlný způsob, jak to provést.

> [!NOTE]
> Pokud vytváříte databázovou aplikaci, která potřebuje zpracovat více relací, budete muset použít [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a>CDataConnection::CDataConnection

Instance inicializuje a inicializuje `CDataConnection` objekt.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Parametry

*Ds*<br/>
[v] Odkaz na existující datové připojení.

### <a name="remarks"></a>Poznámky

První přepsání vytvoří `CDataConnection` nový objekt s výchozím nastavením.

Druhé přepsání vytvoří `CDataConnection` nový objekt s nastavením ekvivalentním zadanému objektu datového připojení.

## <a name="cdataconnectioncopy"></a><a name="copy"></a>CDataConnection::Kopírovat

Vytvoří kopii existujícího datového připojení.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Parametry

*Ds*<br/>
[v] Odkaz na existující datové připojení ke kopírování.

## <a name="cdataconnectionopen"></a><a name="open"></a>CDataConnection::Otevřít

Otevře připojení ke zdroji dat pomocí inicializačního řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Parametry

*szInitString*<br/>
[v] Inicializační řetězec pro zdroj dat.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a>CDataConnection::OpenNewSession

Otevře novou relaci pomocí zdroje dat aktuálního objektu připojení.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Parametry

*Relace*<br/>
[dovnitř/ven] Odkaz na nový objekt relace.

### <a name="remarks"></a>Poznámky

Nová relace používá aktuální objekt připojení obsažený objekt dat jako jeho nadřazený objekt a může přistupovat ke všem stejným informacím jako zdroj dat.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a>CDataConnection::operátor BOOL

Určuje, zda je aktuální relace otevřená či nikoli.

### <a name="syntax"></a>Syntaxe

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu **BOOL** (MFC typedef). **PRAVDA** znamená, že aktuální relace je otevřena; **FALSE** znamená, že aktuální relace je uzavřena.

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a>CDataConnection::operátor bool (OLE DB)

Určuje, zda je aktuální relace otevřená či nikoli.

### <a name="syntax"></a>Syntaxe

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Poznámky

Vrátí **bool** (datový typ Jazyka C++). **true** znamená, že aktuální relace je otevřena; **false** znamená, že aktuální relace je uzavřena.

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a>CDataConnection::operátor CDataSource&amp;

Vrátí odkaz na obsažený `CDataSource` objekt.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí odkaz na `CDataSource` obsažený objekt, což `CDataConnection` umožňuje předat `CDataSource` objekt, kde se očekává odkaz.

### <a name="example"></a>Příklad

Pokud máte funkci `func` (například níže), `CDataSource` která přebírá odkaz, můžete místo toho předat `CDataSource&` `CDataConnection` objekt.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a>CDataConnection::operátor CDataSource*

Vrátí ukazatel na obsažený `CDataSource` objekt.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí ukazatel na `CDataSource` obsažený objekt, což `CDataConnection` umožňuje předat `CDataSource` objekt, kde se očekává ukazatel.

Viz [operátor CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) pro příklad použití.

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a>CDataConnection::operátor CSession&amp;

Vrátí odkaz na obsažený `CSession` objekt.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí odkaz na `CSession` obsažený objekt, což `CDataConnection` umožňuje předat `CSession` objekt, kde se očekává odkaz.

### <a name="example"></a>Příklad

Pokud máte funkci `func` (například níže), `CSession` která přebírá odkaz, můžete místo toho předat `CSession&` `CDataConnection` objekt.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a>CDataConnection::operátor CSession*

Vrátí ukazatel na obsažený `CSession` objekt.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí ukazatel na `CSession` obsažený objekt, což `CDataConnection` umožňuje předat `CSession` objekt, kde se očekává ukazatel.

### <a name="example"></a>Příklad

Viz [operátor CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md) pro příklad použití.

## <a name="see-also"></a>Viz také

[Šablony spotřebitelů OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Odkaz na šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
