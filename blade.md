## Blade Template Engine

### Showing variables

```
{{ $slot }}
```

### Showing Unescaped Data

```
{!! $name !!}
```

### If Statement

```
@if (count($records) === 1)
    I have one record!
@elseif (count($records) > 1)
    I have multiple records!
@else
    I don't have any records!
@endif
```

### For Loop

```
@for ($i = 0; $i < 10; $i++)
    The current value is {{ $i }}
@endfor
```

### Foreach Loop

```
@foreach ($users as $user)
    <p>This is user {{ $user->id }}</p>
@endforeach
```

### Method Field

```
@method('DELETE')
```

### Include Views

```
@include('shared.errors')
```

### Extend View

```
@extends('layouts.app')
```
### Yield Content

```
@yield('content')
```

### Sections

```
@section('sidebar')
    <p>This is appended to the master sidebar.</p>
@endsection
```

### CSRF Field

```
@csrf
```