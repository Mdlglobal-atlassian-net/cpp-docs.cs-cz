---
title: '&lt;system_error –&gt; výčty | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- system_error/std::errc
- system_error/std::io_errc
ms.assetid: b21321b7-404a-40de-8777-a85b77c6fa58
ms.openlocfilehash: 4b288d163f5388d2f021b85f29854924a3ed3424
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ltsystemerrorgt-enums"></a>&lt;system_error –&gt; výčty

|||
|-|-|
|[errc](#errc)|[io_errc](#io_errc)|

## <a name="errc"></a>  errc – výčet

Poskytuje symbolický názvy pro všechny makra kód chyby definované Posix v `<errno.h>`.

errc – třída {address_family_not_supported = EAFNOSUPPORT, address_in_use = EADDRINUSE, address_not_available = EADDRNOTAVAIL, already_connected = EISCONN, argument_list_too_long = e2big –, argument_out_of_domain = edom –, bad_address = CHOZÍ bad_file_ Popisovač = ebadf –, bad_message = EBADMSG, broken_pipe = EPIPE, connection_aborted = ECONNABORTED, connection_already_in_progress = EALREADY, connection_refused = ECONNREFUSED, connection_reset = ECONNRESET cross_device_link = EXDEV –, destination_ address_required = EDESTADDRREQ, device_or_resource_busy = EBUSY, directory_not_empty = ENOTEMPTY, executable_format_error = enoexec –, file_exists = eexist –, file_too_large = EFBIG, filename_too_long = ENAMETOOLONG, function_not_supported = ENOSYS, host_unreachable = EHOSTUNREACH, identifier_removed = EIDRM, illegal_byte_sequence = eilseq –, inappropriate_io_control_operation = ENOTTY, přerušena = EINTR, invalid_argument = einval –, invalid_seek = ESPIPE, io_error = EIO is_a_directory = EISDIR, message_size = EMSGSIZE, network_down = ENETDOWN, network_reset = ENETRESET, network_unreachable = ENETUNREACH, no_buffer_space = ENOBUFS, no_child_process = echild –, no_link = ENOLINK, no_lock_available = ENOLCK, no_message_available = ENODATA, no_ zpráva = ENOMSG, no_protocol_option = ENOPROTOOPT, no_space_on_device = enospc –, no_stream_resources = ENOSR, no_such_device_or_address = ENXIO, no_such_device = ENODEV, no_such_file_or_directory = enoent –, no_such_process = ESRCH, not_a_directory = ENOTDIR, not_a_socket = ENOTSOCK, not_a_stream = ENOSTR, not_connected = ENOTCONN, not_enough_memory = enomem –, not_supported = ENOTSUP, operation_canceled = ECANCELED, operation_in_progress = EINPROGRESS, operation_not_permitted = EPERM, operation_ NOT_SUPPORTED = EOPNOTSUPP, operation_would_block = EWOULDBLOCK, owner_dead = EOWNERDEAD, permission_denied = eacces –, protocol_error = EPROTO, protocol_not_supported = EPROTONOSUPPORT, read_only_file_system = EROFS, resource_deadlock_would_occur = EDEADLK, resource_unavailable_try_again = eagain –, result_out_of_range = erange –, state_not_recoverable = ENOTRECOVERABLE, stream_timeout = ETIME, text_file_busy = ETXTBSY, timed_out = ETIMEDOUT, too_many_files_open_in_system = ENFILE too_many_ files_open = emfile –, too_many_links = EMLINK, too_many_synbolic_link_levels = ELOOP, value_too_large = EOVERFLOW, wrong_protocol_type = EPROTOTYPE,};

### <a name="remarks"></a>Poznámky

## <a name="io_errc"></a>  io_errc – výčet

Poskytuje symbolický názvy pro chybové stavy v \<iostream >. Slouží k vytvoření [error_condition](../standard-library/error-condition-class.md) objekty, které se má porovnat s hodnotou, kterou vrátí [ios_base::failure](../standard-library/ios-base-class.md#failure) `code()` funkce.

io_errc – třída {datového proudu = 1};

### <a name="remarks"></a>Poznámky

Obě [std::make_error_code()](../standard-library/system-error-functions.md#make_error_code) a [std::make_error_condition()](../standard-library/system-error-functions.md#make_error_condition) jsou přetížené pro tento výčet.

`ios_base::failure` může obsahovat jiné než kategorie kódy chyb `error_condition`.

### <a name="example"></a>Příklad

```cpp
// io_errc.cpp
// cl.exe /nologo /W4 /EHsc /MTd

#include <iostream>

using namespace std;

int main()
{
    cin.exceptions(ios::failbit | ios::badbit);

    try {
        cin.rdbuf(nullptr); // throws io_errc::stream
    }
    catch (ios::failure& e) {
        cerr << "ios failure caught: ";
        if (e.code() == make_error_condition(io_errc::stream)) {
            cerr << "io_errc stream error condition" << endl;
        }
        else {
            cerr << "unmatched error condition code " << e.code() << endl;
        }
    }
}
```

## <a name="see-also"></a>Viz také

[<system_error>](../standard-library/system-error.md)<br/>
