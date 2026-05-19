<script>
    let actionBtn;

    function handleAction() {
        const checked = Array.from(document.querySelectorAll('input[type="checkbox"]:checked'));
        const ids = checked.map(cb => cb.id);
        console.log('selected ids:', ids);
    }
</script>

<div class=" flex flex-col items-center mt-10 gap-5">
    <button
        class="text-4xl px-8 py-4 bg-blue-600 hover:bg-blue-700 text-white font-medium rounded-md shadow-md"
        bind:this={actionBtn}
        onclick={handleAction}>Action</button
    >
    <div class="flex flex-wrap gap-5">
        <div>
            <div>
                <input type="checkbox" id="1" />
                <label for="1">1</label>
            </div>
            <div>
                <input type="checkbox" id="2" />
                <label for="2">2</label>
            </div>
            <div>
                <input type="checkbox" id="3" />
                <label for="3">3</label>
            </div>
            <div>
                <input type="checkbox" id="4" />
                <label for="4">4</label>
            </div>
            <div>
                <input type="checkbox" id="5" />
                <label for="5">5</label>
            </div>
            <div>
                <input type="checkbox" id="6" />
                <label for="6">6</label>
            </div>
            <div>
                <input type="checkbox" id="7" />
                <label for="7">7</label>
            </div>
            <div>
                <input type="checkbox" id="8" />
                <label for="8">8</label>
            </div>
            <div>
                <input type="checkbox" id="9" />
                <label for="9">9</label>
            </div>
            <div>
                <input type="checkbox" id="10" />
                <label for="10">10</label>
            </div>
        </div>
        <div>
            <div>
                <input type="checkbox" id="11" />
                <label for="11">11</label>
            </div>
            <div>
                <input type="checkbox" id="12" />
                <label for="12">12</label>
            </div>
            <div>
                <input type="checkbox" id="13" />
                <label for="13">13</label>
            </div>
            <div>
                <input type="checkbox" id="14" />
                <label for="14">14</label>
            </div>
            <div>
                <input type="checkbox" id="15" />
                <label for="15">15</label>
            </div>
            <div>
                <input type="checkbox" id="16" />
                <label for="16">16</label>
            </div>
            <div>
                <input type="checkbox" id="17" />
                <label for="17">17</label>
            </div>
            <div>
                <input type="checkbox" id="18" />
                <label for="18">18</label>
            </div>
            <div>
                <input type="checkbox" id="19" />
                <label for="19">19</label>
            </div>
            <div>
                <input type="checkbox" id="20" />
                <label for="20">20</label>
            </div>
        </div>
        <div>
            <div>
                <input type="checkbox" id="21" />
                <label for="21">21</label>
            </div>
            <div>
                <input type="checkbox" id="22" />
                <label for="22">22</label>
            </div>
            <div>
                <input type="checkbox" id="23" />
                <label for="23">23</label>
            </div>
            <div>
                <input type="checkbox" id="24" />
                <label for="24">24</label>
            </div>
            <div>
                <input type="checkbox" id="25" />
                <label for="25">25</label>
            </div>
            <div>
                <input type="checkbox" id="26" />
                <label for="26">26</label>
            </div>
            <div>
                <input type="checkbox" id="27" />
                <label for="27">27</label>
            </div>
            <div>
                <input type="checkbox" id="28" />
                <label for="28">28</label>
            </div>
            <div>
                <input type="checkbox" id="29" />
                <label for="29">29</label>
            </div>
            <div>
                <input type="checkbox" id="30" />
                <label for="30">30</label>
            </div>
        </div>
        <div>
            <div>
                <input type="checkbox" id="31" />
                <label for="31">31</label>
            </div>
            <div>
                <input type="checkbox" id="32" />
                <label for="32">32</label>
            </div>
            <div>
                <input type="checkbox" id="33" />
                <label for="33">33</label>
            </div>
            <div>
                <input type="checkbox" id="34" />
                <label for="34">34</label>
            </div>
            <div>
                <input type="checkbox" id="35" />
                <label for="35">35</label>
            </div>
            <div>
                <input type="checkbox" id="36" />
                <label for="36">36</label>
            </div>
            <div>
                <input type="checkbox" id="37" />
                <label for="37">37</label>
            </div>
            <div>
                <input type="checkbox" id="38" />
                <label for="38">38</label>
            </div>
            <div>
                <input type="checkbox" id="39" />
                <label for="39">39</label>
            </div>
            <div>
                <input type="checkbox" id="40" />
                <label for="40">40</label>
            </div>
        </div>
    </div>
</div>
