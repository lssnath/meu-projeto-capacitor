<script>
    let display=$state('');
    function clear(){}

    function calc (){}
    display = eval (display);
    function press(c) {
        display+=c;
    }
</script>

<div class="text-center mt-3">
   <input class="form-control" readonly bind:value={display}
   <table class="table table-sm table-borderless">
    <tbody>
        <tr>
<td><button type="button" class="btn-danger w-100">C</
    button></td>
    <td><button type="button" class="btn btn-primary w-100">&lpar;
        </button></td>
        <td><button type="button" class="btn btn-primary w-100">&rpar;
            </button></td>
            <td><button type="button" class="btn bg-primary-suble w-100">/
                </button></td>
        </tr>
        <tr>
            <td><button type="button" class="btn btn-primary w-100">7</
                button></td>
                <td><button type="button" class="btn btn-primary w-100">8</
                    button></td>
                    <td><button type="button" class="btn btn-primary w-100">9</
                        button></td>
                        <td><button type="button" class="btn bg-primary-subtle
                            w-100">x</button></td>
        </tr>
        <tr>
            <td><button class="btn btn-primary w-100">4</button></td>
            <td><button class="btn btn-primary w-100">5</button></td>
            <td><button class="btn btn-primary w-100">6</button></td>
            <td><button class="btn bg-primary-subtle w-100">-</button></td>
        </tr>
        <tr>
            <td><button class="btn btn-primary w-100">1</button></td>
            <td><button class="btn btn-primary w-100">2</button></td>
            <td><button class="btn btn-primary w-100">3</button></td>
            <td rowspan="2" style="height: 0;">
                <button class="btn bg-primary-subtle w-100 h-100">+</button>
            </td>
        </tr>
        <tr>
            <td><button class="btn btn-primary w-100">0</button></td>
            <td><button class="btn btn-primary w-100">.</button></td>
            <td><button class="btn bg-primary-subtle w-100">=</button></td>
        </tr>
    </tbody>
   </table>
</div>


                               
                                                
