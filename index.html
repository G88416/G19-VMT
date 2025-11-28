<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>G19 VMT - Advanced Minute Transcribing Application</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #e0f7fa;
            padding: 20px;
            text-align: center;
            color: #333;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: #ffffff;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }
        h1 {
            color: #00796b;
        }
        button {
            padding: 12px 24px;
            margin: 10px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            border-radius: 6px;
            background-color: #009688;
            color: white;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #00796b;
        }
        button:disabled {
            background-color: #b2dfdb;
            cursor: not-allowed;
        }
        #transcript, #minutesContent {
            width: 100%;
            min-height: 200px;
            border: 1px solid #ccc;
            padding: 15px;
            margin-top: 20px;
            text-align: left;
            background-color: #f9f9f9;
            border-radius: 6px;
        }
        #minutes {
            margin-top: 30px;
            display: none;
        }
        #status {
            margin-top: 15px;
            font-style: italic;
            color: #555;
        }
        #language {
            margin-top: 15px;
            color: #00796b;
        }
        .edit-mode #minutesContent {
            border: 1px solid #009688;
            background-color: #e0f7fa;
        }
        .file-upload {
            margin: 20px 0;
            display: inline-block;
            position: relative;
            overflow: hidden;
        }
        .file-upload input {
            position: absolute;
            left: 0;
            top: 0;
            opacity: 0;
            cursor: pointer;
        }
        .file-upload button {
            background-color: #4caf50;
        }
        .file-upload button:hover {
            background-color: #388e3c;
        }
        #audioPlayback {
            margin-top: 20px;
        }
        a {
            color: #009688;
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }
        #collaboration {
            margin-top: 30px;
            padding: 15px;
            background-color: #f0f8ff;
            border-radius: 6px;
        }
        #meetingId {
            padding: 10px;
            width: 300px;
            margin: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        #onlineUsers {
            margin-top: 20px;
            text-align: left;
        }
        #onlineUsers ul {
            list-style-type: none;
            padding: 0;
        }
        #onlineUsers li {
            background: #dff0d8;
            margin: 5px 0;
            padding: 10px;
            border-radius: 4px;
        }
        #videoSection {
            margin-top: 30px;
            display: none;
        }
        #localVideoContainer, #remoteVideos {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
        }
        .video-container {
            margin: 10px;
            text-align: center;
        }
        video {
            width: 320px;
            height: 240px;
            border: 1px solid #ccc;
            background: black;
            border-radius: 6px;
        }
        .video-label {
            margin-top: 5px;
            font-size: 14px;
            color: #333;
        }
    </style>
    <script src="https://cdn.jsdelivr.net/npm/@xenova/transformers@3.0.0"></script>
    <script src="https://raw.githubusercontent.com/nitotm/efficient-language-detector-js/main/minified/eld.M60.min.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-database-compat.js"></script>
</head>
<body>
    <div class="container">
        <h1>G19 VMT</h1>
        <p>Advanced Voice Meeting Transcriber with Real-time Collaboration and Multi-User Video</p>
        
        <button id="startBtn">Start Recording</button>
        <button id="stopBtn" disabled>Stop Recording</button>
        <button id="interpretBtn" disabled>Interpret and Generate Minutes</button>
        
        <div class="file-upload">
            <button>Upload Audio Recording</button>
            <input type="file" id="audioUpload" accept="audio/*">
        </div>
        
        <div id="status"></div>
        <div id="language">Detected Language: <span id="detectedLang">Unknown</span></div>
        
        <div id="transcript"></div>
        
        <div id="minutes">
            <h2>Generated Minutes</h2>
            <div id="minutesContent"></div>
            <button id="editBtn">Edit Minutes</button>
            <button id="saveBtn" style="display: none;">Save Changes</button>
        </div>
        
        <div id="collaboration" style="display: none;">
            <h3>Real-time Collaboration</h3>
            <input type="text" id="meetingId" placeholder="Enter Meeting ID">
            <button id="createCollabBtn">Create New Session</button>
            <button id="joinCollabBtn">Join Session</button>
            <p id="collabStatus"></p>
            <div id="onlineUsers">
                <h4>Online Users:</h4>
                <ul id="userList"></ul>
            </div>
        </div>
        
        <div id="videoSection">
            <h3>Video Conference</h3>
            <div id="localVideoContainer">
                <div class="video-container">
                    <video id="localVideo" autoplay playsinline muted></video>
                    <div class="video-label">You</div>
                </div>
            </div>
            <div id="remoteVideos"></div>
            <button id="startVideoBtn" disabled>Start Video</button>
            <button id="shareScreenBtn" disabled>Share Screen</button>
            <button id="stopShareBtn" style="display: none;">Stop Sharing</button>
        </div>
        
        <audio id="audioPlayback" controls style="display: none; margin-top: 20px;"></audio>
        <a id="downloadLink" style="display: none; margin-left: 10px;">Download Audio</a>
    </div>

    <script>
        // Firebase Configuration - Replace with your own
        const firebaseConfig = {
            apiKey: "YOUR_API_KEY",
            authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
            projectId: "YOUR_PROJECT_ID",
            storageBucket: "YOUR_PROJECT_ID.appspot.com",
            messagingSenderId: "YOUR_SENDER_ID",
            appId: "YOUR_APP_ID",
            databaseURL: "https://YOUR_PROJECT_ID.firebaseio.com"
        };

        const app = firebase.initializeApp(firebaseConfig);
        const db = firebase.firestore();
        const rtdb = firebase.database();

        const startBtn = document.getElementById('startBtn');
        const stopBtn = document.getElementById('stopBtn');
        const interpretBtn = document.getElementById('interpretBtn');
        const audioUpload = document.getElementById('audioUpload');
        const transcriptDiv = document.getElementById('transcript');
        const statusDiv = document.getElementById('status');
        const detectedLangSpan = document.getElementById('detectedLang');
        const minutesDiv = document.getElementById('minutes');
        const minutesContent = document.getElementById('minutesContent');
        const editBtn = document.getElementById('editBtn');
        const saveBtn = document.getElementById('saveBtn');
        const collaborationDiv = document.getElementById('collaboration');
        const meetingIdInput = document.getElementById('meetingId');
        const createCollabBtn = document.getElementById('createCollabBtn');
        const joinCollabBtn = document.getElementById('joinCollabBtn');
        const collabStatus = document.getElementById('collabStatus');
        const userList = document.getElementById('userList');
        const videoSection = document.getElementById('videoSection');
        const localVideo = document.getElementById('localVideo');
        const remoteVideos = document.getElementById('remoteVideos');
        const startVideoBtn = document.getElementById('startVideoBtn');
        const shareScreenBtn = document.getElementById('shareScreenBtn');
        const stopShareBtn = document.getElementById('stopShareBtn');
        const audioPlayback = document.getElementById('audioPlayback');
        const downloadLink = document.getElementById('downloadLink');

        let mediaRecorder;
        let audioChunks = [];
        let recognition;
        let transcript = '';
        let finalTranscript = '';
        let detectedLanguage = 'en';
        let asr;
        let summarizer;
        let translator;
        let docRef = null;
        let unsubscribe = null;
        let isEditing = false;
        let username = '';
        let userId = '';
        let meetingId = '';
        let localStream = null;
        let isSharingScreen = false;
        let screenTrack = null;
        let peerConnections = {}; // {remoteUserId: {pc: RTCPeerConnection, video: HTMLVideoElement, label: HTMLDivElement}}

        const servers = {
            iceServers: [
                { urls: ['stun:stun1.l.google.com:19302', 'stun:stun2.l.google.com:19302'] },
            ],
            iceCandidatePoolSize: 10,
        };

        // Initialize Transformers.js pipelines
        async function initPipelines() {
            statusDiv.textContent = 'Loading AI models...';
            try {
                const { pipeline } = Xenova;
                asr = await pipeline('automatic-speech-recognition', 'Xenova/whisper-tiny.en');
                translator = await pipeline('translation', 'Xenova/nllb-200-distilled-600M');
                summarizer = await pipeline('summarization', 'Xenova/bart-large-cnn');
                statusDiv.textContent = 'AI models loaded.';
            } catch (error) {
                console.error('Error loading models:', error);
                statusDiv.textContent = 'Error loading AI models.';
            }
        }

        initPipelines();

        // Debounce function
        function debounce(func, delay) {
            let timeout;
            return (...args) => {
                clearTimeout(timeout);
                timeout = setTimeout(() => func(...args), delay);
            };
        }

        // Live Recording (unchanged)
        startBtn.addEventListener('click', async () => {
            statusDiv.textContent = 'Requesting microphone access...';
            try {
                const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
                mediaRecorder = new MediaRecorder(stream);
                audioChunks = [];

                mediaRecorder.ondataavailable = (event) => {
                    audioChunks.push(event.data);
                };

                mediaRecorder.onstop = () => {
                    const audioBlob = new Blob(audioChunks, { type: 'audio/webm' });
                    const audioUrl = URL.createObjectURL(audioBlob);
                    audioPlayback.src = audioUrl;
                    audioPlayback.style.display = 'block';
                    downloadLink.href = audioUrl;
                    downloadLink.download = 'recording.webm';
                    downloadLink.textContent = 'Download Audio';
                    downloadLink.style.display = 'inline';
                };

                const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
                recognition = new SpeechRecognition();
                recognition.continuous = true;
                recognition.interimResults = true;
                recognition.lang = 'en-US';

                recognition.onresult = (event) => {
                    let interimTranscript = '';
                    for (let i = event.resultIndex; i < event.results.length; i++) {
                        const trans = event.results[i][0].transcript;
                        if (event.results[i].isFinal) {
                            finalTranscript += trans + ' ';
                        } else {
                            interimTranscript += trans;
                        }
                    }
                    transcript = finalTranscript + interimTranscript;
                    transcriptDiv.textContent = transcript;

                    if (finalTranscript.length > 20 && detectedLanguage === 'en') {
                        const result = eld.detect(finalTranscript);
                        if (result.isReliable() && result.language !== 'en') {
                            detectedLanguage = result.language;
                            detectedLangSpan.textContent = detectedLanguage;
                            recognition.lang = `${detectedLanguage}-${detectedLanguage.toUpperCase()}`;
                            statusDiv.textContent = `Language detected: ${detectedLanguage}. Switching recognition.`;
                        }
                    }
                };

                recognition.onerror = (event) => {
                    console.error('Recognition error:', event.error);
                    statusDiv.textContent = `Error: ${event.error}`;
                };

                recognition.onend = () => {
                    startBtn.disabled = false;
                    stopBtn.disabled = true;
                    interpretBtn.disabled = false;
                    statusDiv.textContent = 'Recording stopped.';
                };

                mediaRecorder.start();
                recognition.start();
                startBtn.disabled = true;
                stopBtn.disabled = false;
                statusDiv.textContent = 'Recording...';
            } catch (error) {
                console.error('Error accessing microphone:', error);
                statusDiv.textContent = 'Error accessing microphone. Please check permissions.';
            }
        });

        stopBtn.addEventListener('click', () => {
            if (mediaRecorder) mediaRecorder.stop();
            if (recognition) recognition.stop();
        });

        // Upload Audio (unchanged)
        audioUpload.addEventListener('change', async (event) => {
            const file = event.target.files[0];
            if (!file) return;

            statusDiv.textContent = 'Processing uploaded audio...';
            try {
                const audioUrl = URL.createObjectURL(file);
                audioPlayback.src = audioUrl;
                audioPlayback.style.display = 'block';
                downloadLink.href = audioUrl;
                downloadLink.download = file.name;
                downloadLink.textContent = 'Download Uploaded Audio';
                downloadLink.style.display = 'inline';

                const audioData = await fetch(audioUrl).then(res => res.arrayBuffer());
                const transcription = await asr(audioData, { return_timestamps: false });
                finalTranscript = transcription.text;
                transcript = finalTranscript;
                transcriptDiv.textContent = transcript;

                const result = eld.detect(finalTranscript);
                if (result.isReliable()) {
                    detectedLanguage = result.language;
                    detectedLangSpan.textContent = detectedLanguage;
                }

                interpretBtn.disabled = false;
                statusDiv.textContent = 'Audio uploaded and transcribed.';
            } catch (error) {
                console.error('Error processing audio:', error);
                statusDiv.textContent = 'Error processing uploaded audio.';
            }
        });

        // Generate Minutes (unchanged)
        interpretBtn.addEventListener('click', async () => {
            if (!transcript) {
                statusDiv.textContent = 'No transcript available.';
                return;
            }
            statusDiv.textContent = 'Generating minutes...';
            try {
                let textToSummarize = finalTranscript || transcript;

                if (detectedLanguage !== 'en') {
                    statusDiv.textContent = 'Translating to English...';
                    const translationResult = await translator(textToSummarize, { tgt_lang: 'eng_Latn' });
                    textToSummarize = translationResult[0].translation_text;
                }

                const summary = await summarizer(textToSummarize, {
                    max_length: 250,
                    min_length: 50,
                    do_sample: false,
                });
                minutesContent.textContent = summary[0].summary_text;
                minutesDiv.style.display = 'block';
                collaborationDiv.style.display = 'block';
                editBtn.style.display = 'inline';
                saveBtn.style.display = 'none';
                statusDiv.textContent = 'Minutes generated. You can now start real-time collaboration.';
            } catch (error) {
                console.error('Error generating minutes:', error);
                statusDiv.textContent = 'Error generating minutes.';
            }
        });

        // Create New Collaboration Session
        createCollabBtn.addEventListener('click', () => {
            username = prompt('Enter your username:');
            if (!username) return;
            userId = crypto.randomUUID();
            meetingId = crypto.randomUUID();
            meetingIdInput.value = meetingId;
            joinCollaboration(meetingId);
            collabStatus.textContent = `New session created: ${meetingId}. Share this ID to collaborate.`;
            videoSection.style.display = 'block';
            startVideoBtn.disabled = false;
        });

        // Join Collaboration Session
        joinCollabBtn.addEventListener('click', () => {
            username = prompt('Enter your username:');
            if (!username) return;
            userId = crypto.randomUUID();
            meetingId = meetingIdInput.value.trim();
            if (!meetingId) {
                collabStatus.textContent = 'Please enter a Meeting ID.';
                return;
            }
            joinCollaboration(meetingId);
            collabStatus.textContent = `Joined session: ${meetingId}.`;
            videoSection.style.display = 'block';
            startVideoBtn.disabled = false;
        });

        function joinCollaboration(mId) {
            meetingId = mId;
            if (unsubscribe) unsubscribe();
            docRef = db.collection('meetings').doc(meetingId);

            unsubscribe = docRef.onSnapshot((doc) => {
                if (doc.exists) {
                    const data = doc.data();
                    if (data.minutes && !isEditing) {
                        minutesContent.textContent = data.minutes;
                    }
                }
            });

            docRef.get().then((doc) => {
                if (!doc.exists) {
                    docRef.set({ minutes: minutesContent.textContent });
                }
            });

            setupPresence(meetingId, userId, username);
        }

        // Setup User Presence and Handle Joins/Leaves
        function setupPresence(meetingId, userId, username) {
            const userStatusRef = rtdb.ref(`/presence/${meetingId}/${userId}`);

            const connectedRef = rtdb.ref('.info/connected');
            connectedRef.on('value', (snap) => {
                if (snap.val() === true) {
                    userStatusRef.onDisconnect().remove();
                    userStatusRef.set(username);
                }
            });

            // Listen for online users
            const presenceRef = rtdb.ref(`/presence/${meetingId}`);
            presenceRef.on('child_added', (snap) => {
                if (snap.key === userId) return; // Skip self
                const remoteUsername = snap.val();
                const li = document.createElement('li');
                li.id = snap.key;
                li.textContent = remoteUsername;
                userList.appendChild(li);

                // Create peer connection if not exists
                if (!peerConnections[snap.key]) {
                    createRemoteVideo(snap.key, remoteUsername);
                    createPeerConnection(snap.key);
                }
            });

            presenceRef.on('child_removed', (snap) => {
                const liToRemove = document.getElementById(snap.key);
                if (liToRemove) liToRemove.remove();

                // Clean up peer connection
                if (peerConnections[snap.key]) {
                    peerConnections[snap.key].pc.close();
                    peerConnections[snap.key].video.parentNode.remove();
                    delete peerConnections[snap.key];
                }
            });
        }

        // Create remote video container
        function createRemoteVideo(remoteUserId, remoteUsername) {
            const container = document.createElement('div');
            container.className = 'video-container';
            const video = document.createElement('video');
            video.autoplay = true;
            video.playsinline = true;
            const label = document.createElement('div');
            label.className = 'video-label';
            label.textContent = remoteUsername;
            container.appendChild(video);
            container.appendChild(label);
            remoteVideos.appendChild(container);
            peerConnections[remoteUserId] = { video, label, pc: null };
        }

        // Create Peer Connection
        function createPeerConnection(remoteUserId) {
            const pc = new RTCPeerConnection(servers);
            peerConnections[remoteUserId].pc = pc;

            // Add local tracks
            localStream.getTracks().forEach(track => pc.addTrack(track, localStream));

            // Handle remote tracks
            pc.ontrack = (event) => {
                const remoteStream = new MediaStream([event.track]);
                peerConnections[remoteUserId].video.srcObject = remoteStream;
            };

            // ICE connection state
            pc.oniceconnectionstatechange = () => {
                if (pc.iceConnectionState === 'failed' || pc.iceConnectionState === 'disconnected' || pc.iceConnectionState === 'closed') {
                    statusDiv.textContent = `Connection to ${remoteUserId} ${pc.iceConnectionState}.`;
                }
            };

            // Signaling path
            const pairIds = [userId, remoteUserId].sort();
            const signalId = pairIds.join('_');
            const signalRef = docRef.collection('signals').doc(signalId);

            // ICE candidates
            const offerCandidates = signalRef.collection('offerCandidates');
            const answerCandidates = signalRef.collection('answerCandidates');

            pc.onicecandidate = (event) => {
                if (event.candidate) {
                    const candidateCollection = (userId < remoteUserId) ? offerCandidates : answerCandidates;
                    candidateCollection.add(event.candidate.toJSON());
                }
            };

            // Listen for remote candidates
            const remoteCandidateCollection = (userId < remoteUserId) ? answerCandidates : offerCandidates;
            remoteCandidateCollection.onSnapshot(snapshot => {
                snapshot.docChanges().forEach(change => {
                    if (change.type === 'added') {
                        const candidate = new RTCIceCandidate(change.doc.data());
                        pc.addIceCandidate(candidate).catch(error => {
                            console.error('Error adding ICE candidate:', error);
                        });
                    }
                });
            });

            // Decide initiator
            const isInitiator = userId < remoteUserId;

            if (isInitiator) {
                // Create offer
                createOffer(pc, signalRef);
            } else {
                // Listen for offer
                signalRef.onSnapshot(async (snapshot) => {
                    const data = snapshot.data();
                    if (data && data.offer && !pc.remoteDescription) {
                        try {
                            await pc.setRemoteDescription(new RTCSessionDescription(data.offer));
                            const answer = await pc.createAnswer();
                            await pc.setLocalDescription(answer);
                            await signalRef.update({ answer });
                        } catch (error) {
                            console.error('Error handling offer:', error);
                            statusDiv.textContent = 'Error in video connection.';
                        }
                    }
                });
            }

            // Listen for answer if initiator
            if (isInitiator) {
                signalRef.onSnapshot(async (snapshot) => {
                    const data = snapshot.data();
                    if (data && data.answer && !pc.remoteDescription) {
                        try {
                            await pc.setRemoteDescription(new RTCSessionDescription(data.answer));
                        } catch (error) {
                            console.error('Error setting answer:', error);
                            statusDiv.textContent = 'Error in video connection.';
                        }
                    }
                });
            }
        }

        async function createOffer(pc, signalRef) {
            try {
                const offer = await pc.createOffer();
                await pc.setLocalDescription(offer);
                await signalRef.set({ offer });
            } catch (error) {
                console.error('Error creating offer:', error);
                statusDiv.textContent = 'Error starting video call.';
            }
        }

        // Start Video
        startVideoBtn.addEventListener('click', async () => {
            statusDiv.textContent = 'Starting video...';
            try {
                localStream = await navigator.mediaDevices.getUserMedia({ video: true, audio: true });
                localVideo.srcObject = localStream;
                shareScreenBtn.disabled = false;
                startVideoBtn.disabled = true;

                // Add to existing peer connections
                Object.values(peerConnections).forEach(({ pc }) => {
                    if (pc) {
                        localStream.getTracks().forEach(track => pc.addTrack(track, localStream));
                    }
                });

                statusDiv.textContent = 'Video started.';
            } catch (error) {
                console.error('Error starting video:', error);
                if (error.name === 'NotAllowedError') {
                    statusDiv.textContent = 'Camera/microphone access denied. Please grant permissions.';
                } else {
                    statusDiv.textContent = 'Error accessing camera/microphone.';
                }
            }
        });

        // Share Screen
        shareScreenBtn.addEventListener('click', async () => {
            try {
                const screenStream = await navigator.mediaDevices.getDisplayMedia({ video: true });
                screenTrack = screenStream.getVideoTracks()[0];
                const cameraTrack = localStream.getVideoTracks()[0];

                // Replace video track in local stream
                cameraTrack.enabled = false;
                localStream.removeTrack(cameraTrack);
                localStream.addTrack(screenTrack);

                // Replace in all peer connections
                Object.values(peerConnections).forEach(({ pc }) => {
                    const sender = pc.getSenders().find(s => s.track && s.track.kind === 'video');
                    if (sender) sender.replaceTrack(screenTrack);
                });

                screenTrack.onended = stopSharingScreen;
                isSharingScreen = true;
                shareScreenBtn.style.display = 'none';
                stopShareBtn.style.display = 'inline';
                statusDiv.textContent = 'Screen sharing started.';
            } catch (error) {
                console.error('Error sharing screen:', error);
                if (error.name === 'NotAllowedError') {
                    statusDiv.textContent = 'Screen sharing permission denied.';
                } else {
                    statusDiv.textContent = 'Error sharing screen.';
                }
            }
        });

        // Stop Share
        stopShareBtn.addEventListener('click', stopSharingScreen);

        async function stopSharingScreen() {
            if (!isSharingScreen) return;
            screenTrack.stop();
            localStream.removeTrack(screenTrack);

            try {
                const newStream = await navigator.mediaDevices.getUserMedia({ video: true });
                const newCameraTrack = newStream.getVideoTracks()[0];
                localStream.addTrack(newCameraTrack);

                // Replace in all peer connections
                Object.values(peerConnections).forEach(({ pc }) => {
                    const sender = pc.getSenders().find(s => s.track && s.track.kind === 'video');
                    if (sender) sender.replaceTrack(newCameraTrack);
                });

                localVideo.srcObject = localStream;
                isSharingScreen = false;
                stopShareBtn.style.display = 'none';
                shareScreenBtn.style.display = 'inline';
                statusDiv.textContent = 'Screen sharing stopped.';
            } catch (error) {
                console.error('Error restarting camera:', error);
                statusDiv.textContent = 'Error restarting camera after screen share.';
            }
        }

        // Edit Minutes with debounce
        editBtn.addEventListener('click', () => {
            minutesContent.contentEditable = true;
            minutesDiv.classList.add('edit-mode');
            editBtn.style.display = 'none';
            saveBtn.style.display = 'inline';
            statusDiv.textContent = 'Editing minutes...';
            isEditing = true;

            if (docRef) {
                const debouncedUpdate = debounce(() => {
                    docRef.update({ minutes: minutesContent.textContent });
                }, 500);
                minutesContent.addEventListener('input', debouncedUpdate);
            }
        });

        saveBtn.addEventListener('click', () => {
            minutesContent.contentEditable = false;
            minutesDiv.classList.remove('edit-mode');
            saveBtn.style.display = 'none';
            editBtn.style.display = 'inline';
            statusDiv.textContent = 'Changes saved.';
            isEditing = false;

            if (docRef) {
                docRef.update({ minutes: minutesContent.textContent });
            }
        });
    </script>
</body>
</html>
