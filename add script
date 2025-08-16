const SCRIPT_INTERVAL = 5000;
const MESSAGE =
  "==============================================================================================================================================================================================================";

const IS_DEBUG_MODE = false;
const CONNECTION_WAIT_DURATION = 5000;
const ACTION_GAP_DURATION = 100;

const myScript = async () => {
  IS_DEBUG_MODE && alert("script start");

  if (!getIsDisconnected()) {
    try {
      await sendMessage(MESSAGE);
      await delay(ACTION_GAP_DURATION);
      disconnect();
      await delay(ACTION_GAP_DURATION);
    } catch (err) {
      nextChat();
    }
  }

  nextChat();
};

const initialize = async () => {
  getConnectButton().click();
  await waitForConnection();
  setInterval(myScript, SCRIPT_INTERVAL);
};

const getConnectButton = () =>
  Array.from(document.querySelectorAll("button")).find(
    (el) => el.textContent.trim() === "Connect",
  );

const getIsDisconnected = () => {
  const nextButton = Array.from(document.querySelectorAll("button")).find(
    (el) => ["Okay, next"].includes(el.textContent.trim()),
  );

  return !!nextButton;
};

const getChatInput = () =>
  document.querySelector(
    'div[contenteditable="true"][id="yourContentEditableId"]',
  );

const getSendBtn = () =>
  Array.from(document.querySelectorAll("button")).find(
    (el) => el.textContent.trim() === "Send",
  );

const getEndBtn = () =>
  Array.from(document.querySelectorAll("button")).find((el) =>
    ["End", "Okay, next", "Sure?"].includes(el.textContent.trim()),
  );

const nextChat = () => {
  IS_DEBUG_MODE && alert("next chat");
  const endBtn = getEndBtn();
  endBtn.click();
};

const disconnect = async () => {
  IS_DEBUG_MODE && alert("disconnect");
  const endBtn = getEndBtn();
  endBtn.click();
  await delay(ACTION_GAP_DURATION);
  endBtn.click();
};

const sendMessage = async (message) => {
  IS_DEBUG_MODE && alert("send message");
  const chatInput = getChatInput();
  chatInput.textContent = message;
  chatInput.dispatchEvent(new Event("input", { bubbles: true }));
  await delay(ACTION_GAP_DURATION);
  getSendBtn().click();
};

const waitForConnection = () => delay(CONNECTION_WAIT_DURATION);

const delay = (ms) => new Promise((resolve) => setTimeout(resolve, ms));

initialize();
