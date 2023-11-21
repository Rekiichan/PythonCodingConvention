# PythonCodingConvention
Main Style: PEP 8.

## Indent
Sử dụng 4 white-space.

## Comment code
- Comment ngay trên dòng code muốn mô tả, sau dấu `#` phải có 1 phím cách. 
- Mỗi khi if else thì nên có ít nhất 1 dòng mô tả nếu điều kiện phức tạp
``` python
if __name__ == '__main__':
    # Câu lệnh chỉ được thực thi khi file chứa nó được chạy chỉ định
    print('Hello World!')
```
- Đối với function/class, comment tổng quan về function/class ngay dưới tên hàm, bao gồm mô tả chung của hàm, các parameter truyền vào kèm theo kiểu dữ liệu, dữ liệu và kiểu dữ liệu trả về, mô tả exception được raise (nếu có)

``` python
  def connect_to_next_port(minimum: int) -> int:
    """ Connects to the next available port.

    Args:
      minimum: A port value greater or equal to 1024.

    Returns:
      The new minimum port.

    Raises:
      ConnectionError: If no available port is found.
    """
    if minimum < 1024:
      # Note that this raising of ValueError is not mentioned in the doc
      # string's "Raises:" section because it is not appropriate to
      # guarantee this specific behavioral reaction to API misuse.
      raise ValueError(f'Min. port must be at least 1024, not {minimum}.')

    port = self._find_next_open_port(minimum)
    if port is None:
      raise ConnectionError(
          f'Could not connect to service on port {minimum} or higher.')

    assert port >= minimum, (
        f'Unexpected port {port} when minimum was {minimum}.')
    return port

```

## Imports
- Chỉ sử dụng ```import``` cho các packages và mô-đun, không sử dụng cho các lớp hoặc hàm cá nhân.
- Import module sử dụng địa chỉ tuyệt đối của module.
- Mỗi lệnh ```import``` chỉ được sử dụng để import một 1 module duy nhất 

## Blank-line
- Trong một file (module), phía trên và phía dưới (bao xung quanh) của phần định nghĩa function, class là 02 blank-line.
- Với các function được định nghĩa trong một class thì bao xung quanh của function là 01 blank-line.
- Giữa mỗi class sẽ có 2 khoảng trắng
- Dòng cuối cùng của một file/module là một dòng trống.
- Trong một block code, có thể đặt 01 dòng trống vào vị trí nào đó để code có thể tạo điểm nhấn và dễ nhìn hơn. Ví dụ for, if - else,...

``` python
def is_prime_optimal(number):
    if number in [2, 3, 5]:
        return True
    if number % 2 == 0 or number % 3 == 0 or number % 5 == 0 or number < 2:
        return False
    if number < 49:
        return True
        
    if (number % 7) == 0 or (number % 11) == 0 or (number % 13) == 0 or \
        (number % 17) == 0 or (number % 19) == 0 or (number % 23) == 0 or \
        (number % 29) == 0 or (number % 31) == 0 or (number % 37) == 0 or \
            (number % 41) == 0 or (number % 43) == 0 or (number % 47) == 0:
        return False

    if number < 2809:
        return True

    max_range = int(math.sqrt(number)) + 1
    for value in range(53, max_range, 2):
        if number % value == 0:
            return False
    return True
```

Ref: https://google.github.io/styleguide/pyguide.html#316-naming

Tutorials write: https://www.makeareadme.com
