- Pragma solidity ^0.8.7;
Nghĩa là dùng bản mới hơn 0.8.7 vẫn okie,
>= 0.8.7 < 0.9.0 
Dùng phiên bản solidity từ 0.8.7 đến 0.9.0
=> lưu ý khi compile 2 file .sol thì nên để cùng 1 phiên bản solidy

- Uint nếu ko đc xác định sẽ được tự động hiểu là uint256
Ngoài uint còn kiểu int có thể chọn giá trị < 0
Kiểu dữ liệu bytes max là bytes32.

- Visibility 
 + public: visible externally and internally; create a geter function.
 + private: only visibile in current contract.
 + external: only visibile externally, sb outsite the contract can call thus function.
 + internal: only visibile internally, this contract and it's children contract can call this function

- Gas: "the more stuff in your function the more gas it costs"
    + reading - view, pure ko tốn gas, pure không sử dụng dữ liệu của blokcchain.
    + calling / writing - thực hiện transaction; note: nhưng khi gọi view hay pure trong function này thì cx sẽ tốn gas.

- Struct 
    vd: Person {
        uint a;
        uint b;
    }
    khi lấy ra giá trị thì index của a, b lần lượt là 0, 1
- Array 
    Dynamic array[] vs fixed-sized array[n]
- Memory, Storage, Calldata
    EVM có thể truy cập và lưu thông tin ở 6 nơi // DATA LOCATON
    Stack, Memory: biến tamk thời những có thể sử đổi- kết thúc function sẽ biến mất, Storage: biến của chain có thể sử đổi, Calldata: biến tamk thời nhưng ko thể bị sửa đổi, Code, Logs
    Uint không cần xác định kiểu dữ liệu nhưng string thì cần vì sol biết được uint chỉ thực hiện trong hàm 
    ex: function A(unit a, string memory b)...{}
    data location chỉ dùng cho array, struct, mapping; string = array of byte.

Có thể deploy contract từ 1 contract khác khi sử dụng từ khóa new
image.png

- inheritance and overrides

    overide: khi muốn override funtion A thì A cần là virtual 
    ex:
    contract A1 {
        function A () public virtual {
            .....
        }
    }
    contract A2 is A1 {
        function A() override public {
            ....
        }
    }