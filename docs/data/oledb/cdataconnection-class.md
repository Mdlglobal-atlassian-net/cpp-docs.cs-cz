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
ms.openlocfilehash: 385445081f84f65ff7030466a238a5a96abd63be
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212057"
---
# <a name="cdataconnection-class"></a>CDataConnection – třída

Spravuje připojení ke zdroji dat.

## <a name="syntax"></a>Syntaxe

```cpp
class CDataConnection
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CDataConnection](#cdataconnection)|Konstruktor Vytvoří instanci a inicializuje objekt `CDataConnection`.|
|[Kopií](#copy)|Vytvoří kopii existujícího datového připojení.|
|[Otevírají](#open)|Otevře připojení ke zdroji dat pomocí inicializačního řetězce.|
|[OpenNewSession](#opennewsession)|Otevře novou relaci pro aktuální připojení.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor BOOL](#op_bool)|Určuje, zda je aktuální relace otevřena nebo nikoli.|
|[operátor bool](#op_bool_ole)|Určuje, zda je aktuální relace otevřena nebo nikoli.|
|[CDataSource – operátor &](#op_cdata_amp)|Vrátí odkaz na objekt obsažený `CDataSource`.|
|[operátor CDataSource *](#op_cdata_star)|Vrátí ukazatel na objekt s omezením `CDataSource`.|
|[CSession – operátor &](#op_csession_amp)|Vrátí odkaz na objekt obsažený `CSession`.|
|[operátor CSession *](#op_csession_star)|Vrátí ukazatel na objekt s omezením `CSession`.|

## <a name="remarks"></a>Poznámky

`CDataConnection` je užitečnou třídou pro vytváření klientů, protože zapouzdřuje potřebné objekty (zdroj dat a relace) a některé práce, které je třeba provést při připojování ke zdroji dat.

Bez `CDataConnection`musíte vytvořit objekt `CDataSource`, zavolat jeho metodu [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) a pak vytvořit instanci objektu [CSession](../../data/oledb/csession-class.md) , zavolat jeho [otevřenou](../../data/oledb/csession-open.md) metodu a pak vytvořit objekt [CCommand](../../data/oledb/ccommand-class.md) a volat metody `Open`*.

V `CDataConnection`stačí vytvořit objekt připojení, předat ho inicializačnímu řetězci a pak pomocí tohoto připojení otevřít příkazy. Pokud máte v úmyslu používat připojení k databázi opakovaně, je vhodné připojení ponechat otevřené a `CDataConnection` nabízí pohodlný způsob, jak to provést.

> [!NOTE]
>  Pokud vytváříte databázovou aplikaci, která potřebuje zpracovávat více relací, budete muset použít [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a>CDataConnection:: CDataConnection

Vytvoří instanci a inicializuje objekt `CDataConnection`.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Parametry

*služby*<br/>
pro Odkaz na existující datové připojení.

### <a name="remarks"></a>Poznámky

První přepsání vytvoří nový objekt `CDataConnection` s výchozími nastaveními.

Druhé přepsání vytvoří nový objekt `CDataConnection` s nastavením, který je ekvivalentní objektu datového připojení, který zadáte.

## <a name="cdataconnectioncopy"></a><a name="copy"></a>CDataConnection:: Copy

Vytvoří kopii existujícího datového připojení.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Parametry

*služby*<br/>
pro Odkaz na existující datové připojení, které se má zkopírovat

## <a name="cdataconnectionopen"></a><a name="open"></a>CDataConnection:: Open

Otevře připojení ke zdroji dat pomocí inicializačního řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Parametry

*szInitString*<br/>
pro Inicializační řetězec pro zdroj dat.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a>CDataConnection:: OpenNewSession

Otevře novou relaci s použitím zdroje dat aktuálního objektu připojení.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Parametry

*jednání*<br/>
[in/out] Odkaz na nový objekt relace.

### <a name="remarks"></a>Poznámky

Nová relace používá objekt zdroje dat s aktuálním objektem připojení jako nadřazený objekt a má přístup ke všem stejným informacím jako zdroj dat.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a>CDataConnection:: operator BOOL

Určuje, zda je aktuální relace otevřena nebo nikoli.

### <a name="syntax"></a>Syntaxe

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Poznámky

Vrací hodnotu **bool** (MFC typedef). **True** znamená, že aktuální relace je otevřená. **False** znamená, že aktuální relace je zavřená.

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a>CDataConnection:: operator bool (OLE DB)

Určuje, zda je aktuální relace otevřena nebo nikoli.

### <a name="syntax"></a>Syntaxe

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu **bool** (C++ datový typ). **true** znamená, že aktuální relace je otevřená. **false** znamená, že aktuální relace je zavřená.

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a>CDataConnection:: operator CDataSource&amp;

Vrátí odkaz na objekt obsažený `CDataSource`.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrací odkaz na objekt obsažený `CDataSource`, který umožňuje předat objekt `CDataConnection`, kde je očekáván odkaz na `CDataSource`.

### <a name="example"></a>Příklad

Pokud máte funkci (například `func` níže), která přebírá `CDataSource` odkaz, můžete místo toho předat objekt `CDataConnection` pomocí `CDataSource&`.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a>CDataConnection:: operator CDataSource *

Vrátí ukazatel na objekt s omezením `CDataSource`.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrací ukazatel na objekt s omezením `CDataSource`, který umožňuje předat objekt `CDataConnection`, kde je očekáván `CDataSource` ukazatel.

Příklad použití naleznete v tématu [Operator CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) .

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a>CDataConnection:: operator CSession&amp;

Vrátí odkaz na objekt obsažený `CSession`.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrací odkaz na objekt obsažený `CSession`, který umožňuje předat objekt `CDataConnection`, kde je očekáván odkaz na `CSession`.

### <a name="example"></a>Příklad

Pokud máte funkci (například `func` níže), která přebírá `CSession` odkaz, můžete místo toho předat objekt `CDataConnection` pomocí `CSession&`.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a>CDataConnection:: operator CSession *

Vrátí ukazatel na objekt s omezením `CSession`.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrací ukazatel na objekt s omezením `CSession`, který umožňuje předat objekt `CDataConnection`, kde je očekáván `CSession` ukazatel.

### <a name="example"></a>Příklad

Příklad použití naleznete v tématu [Operator CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md) .

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
