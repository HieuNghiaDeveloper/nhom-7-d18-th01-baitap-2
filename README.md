# nhom-7-d18-th01-baitap-2
Bước 1: Vào trang web mookapi.io
Bước 2: Tạo 1 project mới (Có thể đặt tên tự do) riêng nhóm 7 đặt tên là MyProject
Bước 3: Vào MyProject vừa tạo, chọn New Resource, tiếp theo hãy đặt tên theo cách bạn muốn (nhóm 7 đặt tên là product)
Bước 4: Copy đoạn mã url: "https://6228b3e79fd6174ca82cae6e.mockapi.io/product/" dán vào source code để tiến hành cài đặt (Lấy api của product)


Bước 5: Đây là code lấy api và xóa api của product
 <script>
        $(function () {

            function fetchData() {
                $.ajax({
                    url: "https://6228b3e79fd6174ca82cae6e.mockapi.io/product",
                    method: "GET",
                    dataType: "JSON",
                    async: false,
                    success: function (response) {
                        var html = "";
                        $.each(response, function (key, value) {
                            var index = key + 1;
                            var id = value.id;
                            var name = value.name;
                            var price = value.price;
                            html += '<tr data-id=' + id + '>'
                                + '    <td>' + name + '</td>'
                                + '    <td>' + price + '</td>'
                                + '    <td><button data-id="' + id + '" class="delete-product">Dẻlẻtẻ</button></td>'
                                + ' <tr>';
                        })
                        $("#data").html(html)
                    },
                    error: function (error) {
                        console.error();
                    }
                })
            }
            fetchData();
            
            $(".delete-product").on("click", function () {
                var id = $(this).attr("data-id");
                if ($(this).parent().parent().attr('data-id') == id) {
                    $(this).parent().parent().hide(1000)
                }
                $.ajax({
                    url: "https://6228b3e79fd6174ca82cae6e.mockapi.io/product/" + id,
                    method: "DELETE",
                    dataType: "JSON",
                    async: false,
                    success: function (response) {
                        alert("Delete successfully");
                        // fetchData();



                    },
                    error: function (error) {
                        console.error();
                    }
                })
            })



        })
    </script>
